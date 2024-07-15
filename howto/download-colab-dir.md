## Downloading folders/directories from Google Colab

Welcome back to my journey with InstructLab using WSL! Lately, I have been able to download a model, serve/chat with it, and generate some synthetic data, all locally on my machine and using the [InstructLab documentation](https://github.com/instructlab/instructlab/tree/main). 

However, I discovered a caveat: training the model locally with GPU acceleration required at least 18GB of VRAM. Alas, my RTX 3060 Laptop GPU only had 12GB VRAM. Luckily, Google Colab provides the capability to utilize cloud-based GPUs. 

After training using the NVIDIA T4, I found that I was not able to directly download my model directory. It turns out that Colab (currently, 7/11/2024) allows you to download individual files, not whole directories/folders. This can prove quite clunky and inefficient. 

A good workaround is to convert your target directory into a zip file and download that. Today I will be guiding you through how to download your trained model from Google Colab after you have completed training on it.

To download folders from Colab, do the following in a code cell:

```
!zip -r name_for_zipped_file.zip path_of_the_folder_to_be_zipped
```
`name_for_zipped_file.zip` refers to the name of the zip file you want to create.

`path_of_the_folder_to_be_zipped` refers to the path to the target directory in your Google Colab file manager.

Example:
![image](https://github.com/user-attachments/assets/793de780-6706-41df-8af5-07fdcc4d0d52)

And there you go! You have successfully downloaded your model from Colab! But it doesn’t stop here. You still need to unzip your model file, and I will also be releasing more tutorials as I go through my InstructLab journey, so stay tuned!