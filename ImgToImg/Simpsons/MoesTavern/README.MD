## How to Generate a Digital Painting Detailed Image of Moe's Tavern from (The Simpsons)

This guide assumes intermediate knowledge of Stable Diffusion, Automatic1111, using generative AI models and having to host Stable Diffusion locally or on the cloud. Go to the bottom of the guide for links of the components that you will need. The goal of this guide is to provide a quick step-by-step workflow done only using "instructive prompts & configurations" performed 100% by generative AI (human graphical engineering will yield "better" images).  

**1) Start with a source image of Moe's Tavern (found on the internet)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: MoesTavern-Source.png) - Parameters:  
(Load image and select "Interrogate CLIP" to generate a starting prompt. Remove any specifics of art style and only image description remains as baseline)  
Result: Generated Prompt - "a cartoon of a bar with a pool table and a bar stools and a bar with a television, promotional image, Dean Roger, concept art, american scene painting"  
![Moe's Tavern Source](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Source.jpg)

**2) Generate an AI image of Moe's Tavern using AI (using the #1 source image)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: MoesTavern-Source.jpg) - Parameters:  
Prompt: a town bar with a pool table and a bar stools and a bar with a television, promotional image, cash register on bar, hyperrealism, realistic, hyperdetailed, digital painting  
Steps: 40, Sampler: DPM++ 2S a Karras, CFG scale: 9, Seed: 2816290687, Size: 640x512, Model hash: 4199bcdd14, Model: revAnimated_v122, Clip skip: 2  
ControlNet: "preprocessor: lineart_standard (from white bg & black line), model: control_v11p_sd15_lineart [43d4be0d], weight: 1, starting/ending: (0, 1), resize mode: Crop and Resize, pixel perfect: False, control mode: Balanced, preprocessor params: (512, 64, 64)"  
Result:  640x512 resolution, ControlNet's Lineart preprocessor provides the contours/lines for the Stable Diffusion Model  
![Moe's Tavern Generated](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated.png)  


**3) Upscale the AI image resolution & add Details (using the generated #2 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: MoesTavern-Generated.png) - Parameters:  
Prompt: a town bar with a pool table and a bar stools and a bar with a television, promotional image, cash register on bar, arcade game in corner, hyper-realism, realistic, hyper-detailed, digital painting  
Negative prompt: EasyNegative, (bad_prompt:0.8), watermark, people, pool sticks, bartenders, people on stools  
Steps: 40, Sampler: DDIM, CFG scale: 8, Seed: 2566453285, Size: 1280x1024, Model hash: 4199bcdd14, Model: revAnimated_v122, Denoising strength: 0.36, Denoising strength change factor: 1, Add Detail: Medium, Add Blur: None, Smoothing: None, Contour: False, Sharpness: 1.12, Brightness: 1, Color Strength: 1, Contrast: 1.04  
Script: Loopback Scaler  
Result:  1280x1024 resolution, Loopback Scaler script increases the image resolution while adding new detail to the image  
![Moe's Tavern Generated-LoopUpscaled](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated-LoopUpscaled.png)  


**4) Inpaint the AI image with some fixes using AI (using the generated #3 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg-InPaint (Image: MoesTavern-LoopUpscaled.png) - Parameters:  
In InPaint: Draw the masks where you want to improve the image. Illustrative (real-scenario would include graphics software)  
Prompt: pool table, pool table pocket, hyper-realism, realistic, hyper-detailed, digital painting  
Negative prompt: EasyNegative, (bad_prompt:0.8), watermark, people, pool sticks, bartenders, people on stools  
Steps: 40, Sampler: DDIM, CFG scale: 8, Seed: 434893738, Size: 1280x1024, Model hash: 8836c40038, Model: revAnimated_v121Inp-inpainting, Denoising strength: 0.46, Conditional mask weight: 1.0, Mask blur: 16  
Result:  1280x1024 resolution, Inpainting with AI can touch up some glaring spots in the generated images  
![Moe's Tavern Generated-LoopUpscaled-Inpaint](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated-LoopUpscaled-Inpaint.png)  

**5) Upscale the AI image resolution & refine the details (using the generated #4 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: MoesTavern-Generated-LoopUpscaled-Inpaint.png) - Parameters:  
Prompt: pool table, pool table pocket, hyper-realism, realistic, hyper-detailed, digital painting  
Negative prompt: EasyNegative, (bad_prompt:0.8), watermark, people, pool sticks, bartenders, people on stools  
Steps: 40, Sampler: DDIM, CFG scale: 8, Seed: 3787160828, Size: 5120x4096, Model hash: e6415c4892, Model: realisticVisionV20_v20, Denoising strength: 0.18, Clip skip: 2, Ultimate SD upscale upscaler: 4x-UltraSharp, Ultimate SD upscale tile_width: 512, Ultimate SD upscale tile_height: 512, Ultimate SD upscale mask_blur: 8, Ultimate SD upscale padding: 32  
Result:  5120x4096 resolution, Ultimate SD Upscaler brings out more detail & increases reolution to 4K+, ControlNet Tiling allows for very large image size without running out of GPU memory  
![Moe's Tavern Generated-4KPlus](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/MoesTavern/MoesTavern-Generated-4KPlus.jpg)  

**Required Components**
1) Automatic1111 Stable Diffusion UI: https://github.com/AUTOMATIC1111/stable-diffusion-webui  
2) ControlNet: https://github.com/lllyasviel/ControlNet  
3) ReVAnimated Stable Diffusion AI Model: https://civitai.com/models/7371?modelVersionId=46846  
4) Loopback Scaler (Python Script for improving image quality): https://github.com/Elldreth/loopback_scaler  
5) EasyNegative (Negative Embeddings): https://civitai.com/models/7808/easynegative  
6) BadPrompt (Negative Embeddings): https://civitai.com/models/55700/badprompt-negative-embedding  
