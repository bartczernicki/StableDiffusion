## How to Generate a Digital Painting Detailed Image of Moe From (The Simpsons)

This guide assumes intermediate knowledge of Stable Diffusion, Automatic1111, using generative AI models and having to host Stable Diffusion locally or on the cloud. Go to the bottom of the guide for links of the components that you will need. The goal of this guide is to provide a quick step-by-step workflow done only using "instructive prompts & configurations" performed 100% by generative AI (human graphical engineering will yield "better" images).  

**1) Start with a source image of Moe**  
![Moe Source](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Source.jpg)

**2) Generate an AI image of Moe using AI (using the #1 source image)**  
![Moe Generated](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated.png)

**3) Inpaint the AI image with some fixes using AI (using the generated #2 AI image)**  
![Moe Generated-Inpaint](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-InpaintTouchup.png)

**4) Upscale the AI image resolution & add Details (using the generated #3 AI image)**  
![Moe Generated-LoopUpscaled](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-LoopUpscaled.png)

**5) Inpaint the AI image with some fixes using AI (using the generated #4 AI image)**  
![Moe Generated-LoopUpscaled-Inpaint](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-LoopUpscaled-InpaintTouchup.png)

**6) Upscale the AI image resolution & refine the details (using the generated #5 AI image)**  
![Moe Generated-4KPlus](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-4KPlus.jpg)

Required Components
1) Automatic1111 Stable Diffusion UI: https://github.com/AUTOMATIC1111/stable-diffusion-webui  
2) ControlNet: https://github.com/lllyasviel/ControlNet  
3) ReVAnimated Stable Diffusion AI Model: https://civitai.com/models/7371?modelVersionId=46846  
4) Loopback Scaler (Python Script for improving image quality): https://github.com/Elldreth/loopback_scaler  
5) EasyNegative (Negative Embeddings): https://civitai.com/models/7808/easynegative  
6) BadPrompt (Negative Embeddings): https://civitai.com/models/55700/badprompt-negative-embedding  
