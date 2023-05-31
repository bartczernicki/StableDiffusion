## How to Generate a Digital Painting Detailed Image of Moe's Tavern from (The Simpsons)

This guide assumes intermediate knowledge of Stable Diffusion, Automatic1111, using generative AI models and having to host Stable Diffusion locally or on the cloud. Go to the bottom of the guide for links of the components that you will need. 

**1) Start with a source image of Moe's Tavern (found on the internet)**  
![Moe's Tavern Source](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Source.jpg)

**2) Generate an AI image of Moe's Tavern using AI (using the #1 source image)**  
![Moe's Tavern Generated](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated.png)  
Using Automatic1111 StableDiffusion - ImgToImg - Parameters:  
Prompt: a town bar with a pool table and a bar stools and a bar with a television, promotional image, cash register on bar, hyperrealism, realistic, hyperdetailed, digital painting  
Steps: 40, Sampler: DPM++ 2S a Karras, CFG scale: 9, Seed: 2816290687, Size: 640x512, Model hash: 4199bcdd14, Model: revAnimated_v122, Clip skip: 2
ControlNet: "preprocessor: lineart_standard (from white bg & black line), model: control_v11p_sd15_lineart [43d4be0d], weight: 1, starting/ending: (0, 1), resize mode: Crop and Resize, pixel perfect: False, control mode: Balanced, preprocessor params: (512, 64, 64)"  

**3) Upscale the AI image resolution & add Details (using the generated #2 AI image)**  
![Moe's Tavern Generated-LoopUpscaled](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated-LoopUpscaled.png)  

**4) Inpaint the AI image with some fixes using AI (using the generated #3 AI image)**  
![Moe's Tavern Generated-LoopUpscaled-Inpaint](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated-LoopUpscaled-Inpaint.png)  

**5) Upscale the AI image resolution & refine the details (using the generated #4 AI image)**  
![Moe's Tavern Generated-4KPlus](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated-4KPlus.jpg)  

**Required Components**
1) Automatic1111 Stable Diffusion UI: https://github.com/AUTOMATIC1111/stable-diffusion-webui  
2) ControlNet: https://github.com/lllyasviel/ControlNet  
3) ReVAnimated Stable Diffusion AI Model: https://civitai.com/models/7371?modelVersionId=46846  
4) Loopback Scaler (Python Script for improving image quality): https://github.com/Elldreth/loopback_scaler  
5) EasyNegative (Negative Embeddings): https://civitai.com/models/7808/easynegative  
6) BadPrompt (Negative Embeddings): https://civitai.com/models/55700/badprompt-negative-embedding  
