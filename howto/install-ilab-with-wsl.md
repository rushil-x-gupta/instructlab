# Installing InstructLab on Windows using WSL (Windows Subsystem for Linux)

In this tutorial, I will be walking through my full process of running InstructLab on WSL, from installation of WSL to the initialization of InstructLab. My laptop specs are:

- CPU: Intel i7-10750H

- RAM: 16GB

- GPU: Geforce RTX 3060 Laptop GPU (12GB VRAM)


## Installing WSL

To install WSL, first open up Powershell. From here, type the command:

```
wsl --install
```

There you go, WSL is installed! (Quite easy, wasn’t it?) This installs necessary features for WSL and the Ubuntu distro as default. The default distro can be changed with `wsl --list -d <DistributionName>`. As of writing, Fedora is not supported with WSL (I could not figure out how to obtain the tar file for it) so I just proceeded with using Ubuntu. If you would still like to install WSL with Fedora, some links that may help you are listed below:	
- https://dev.to/bowmanjd/install-fedora-on-windows-subsystem-for-linux-wsl-4b26
- https://learn.microsoft.com/en-us/windows/wsl/use-custom-distro

To run WSL, simply type the command

```
wsl
```

and your Linux environment will be set up in Powershell.

## Installing InstructLab 
From here, we can proceed with setting up InstructLab within our Linux environment. First, create a directory called `instructlab` to store the files InstructLab needs to run and cd into that directory:

```	
mkdir instructlab
cd instructlab
```

Next, update and upgrade your Linux environment to ensure all of your installed packages are up-to-date.

```
sudo apt update
sudo apt upgrade
```

For the sake of simplicity, we will be installing InstructLab using PyTorch without CUDA bindings or GPA acceleration. To do that, first go ahead and install the `python3.10-venv` package.

```
sudo apt install python3.10-venv
```

Then,

```
python3 -m venv --upgrade-deps venv
source venv/bin/activate
pip cache remove llama_cpp_python
```

Install cmake:

```
pip install cmake
```

And install build-essential

```
sudo apt install build-essential
```

Finally, install the `instructlab` package. Note that we are making sure the build is done without Apple M-series GPU support.

```
CMAKE_ARGS="-DLLAMA_METAL=off" pip install instructlab --extra-index-url=https://download.pytorch.org/whl/cpu
```

## Running InstructLab
At last, we can run `instructlab`. Verify the `ilab` CLI is running, then initialize it.

```
ilab
ilab config init
```

And there you go! You have InstructLab setup on your Windows machine (using Linux) through WSL! But it doesn’t stop here. You still need to download your model, generate your synthetic test data, train your model, test it, and even talk to it. If you end up not having enough VRAM to train your models locally (like me), you can use a cloud service like Google Colab. I highly recommend checking out the official documentation for these next steps. 
