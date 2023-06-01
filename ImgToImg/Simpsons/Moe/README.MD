## Using Generative AI - Generate a Digital Painting Image of Moe From "The Simpsons"

This guide assumes intermediate knowledge of Stable Diffusion, Automatic1111, using generative AI models and having to host Stable Diffusion locally or on the cloud. Go to the bottom of the guide for links of the components that you will need. The goal of this guide is to provide a quick step-by-step workflow done only using "instructive prompts & configurations" performed 100% by generative AI (human graphical engineering will yield "better" images).  

**1) Start with a source image of Moe with a Shotgun (found on internet)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: Moe-Source.png) - Parameters:  
(Load image and select "Interrogate CLIP" to generate a starting prompt. Remove any specifics of art style (cartoon) and only image description remains as baseline)  
Result - Generated Prompt: - "a cartoon character holding a gun and pointing it at the viewer with a surprised look on his face and a gun in his hand"  
![Moe Source](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Source.jpg)

**2) Generate an AI image of Moe using AI (using the #1 source image)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: Moes-Source.png) - Parameters:
Prompt: middle-aged skinny bar owner with wrinkles pointing a (wood shotgun:1.2) at the viewer, curly grey hair, wearing shirt, hyperrealism, realistic, hyperdetailed, digital painting, bar background  
Negative prompt: EasyNegative, (bad_prompt:0.8), text, watermark, glasses, bald, facial hair, muscular, hat, woman, scope, gun scope, mustache, beard  
Steps: 36, Sampler: DPM++ 2S a Karras, CFG scale: 8, Seed: 1152701863, Size: 600x400, Model hash: 4199bcdd14, Model: revAnimated_v122, Denoising strength: 0.44, Clip skip: 2, Mask blur: 4  
Result - New Image: 600x400 resolution, ControlNet's Lineart preprocessor provides the contours/lines for the Stable Diffusion Model for Moe's pose  
![Moe Generated](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated.png)

**3) Inpaint the AI image with some fixes using AI (using the generated #2 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg - Inpaint (Image: Moe-Generated.png) - Parameters:  
In InPaint: Draw the masks where you want to improve the image. Illustrative (real-scenario would include graphics software)
Prompt: black shotgun muzzle  
Negative prompt: EasyNegative, (bad_prompt:0.8), text, watermark, glasses, bald, facial hair, muscular, hat, woman, scope, gun scope, mustache, beard  
Steps: 36, Sampler: DPM++ 2S a Karras, CFG scale: 8, Seed: 4081638091, Size: 600x400, Model hash: 4199bcdd14, Model: revAnimated_v122, Denoising strength: 0.48, Clip skip: 2, Mask blur: 4  
Result - New Image: 600x400 resolution, Inpaint fixes finger on trigger, gun barrels, less facial hair on Moe  
![Moe Generated-Inpaint](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-InpaintTouchup.png)

**4) Upscale the AI image resolution & add Details (using the generated #3 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: Moe-Generated-InpaintTouchup.png) - Parameters:  
Prompt: middle-aged skinny bar owner with wrinkles pointing a (wood shotgun:1.2) at the viewer, curly grey hair, wearing shirt, hyperrealism, realistic, hyperdetailed, digital painting, bar background  
Negative prompt: EasyNegative, (bad_prompt:0.8), text, watermark, glasses, bald, facial hair, muscular, hat, woman, scope, gun scope, mustache, beard  
Steps: 34, Sampler: DDIM, CFG scale: 8, Seed: 3708888578, Size: 1260x840, Model hash: 4199bcdd14, Model: revAnimated_v122, Denoising strength: 0.32, Clip skip: 2, Denoising strength change factor: 1, Add Detail: High, Add Blur: None, Smoothing: None, Contour: False, Sharpness: 1.2, Brightness: 1, Color Strength: 1, Contrast: 1.04  
Result - New Image: 1256x840 resolution, Loopback Scaler script increases the image resolution while adding new detail to the image  
![Moe Generated-LoopUpscaled](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-LoopUpscaled.png)

**5) Inpaint the AI image with some fixes using AI (using the generated #4 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg (Image: Moe-Generated-LoopUpscaled.png) - Parameters:  
In InPaint: Draw the masks where you want to improve the image. Illustrative (real-scenario would include graphics software)  
Prompt: back of gun trigger  
Negative prompt: trigger  
Steps: 34, Sampler: DDIM, CFG scale: 8, Seed: 2125357317, Size: 1256x840, Model hash: 8836c40038, Model: revAnimated_v121Inp-inpainting, Denoising strength: 0.38, Conditional mask weight: 1.0, Mask blur: 16  
Result - New Image: 1256x840 resolution, Inpaint fixes the back of the trigger
![Moe Generated-LoopUpscaled-Inpaint](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-LoopUpscaled-InpaintTouchup.png)

**6) Upscale the AI image resolution & refine the details (using the generated #5 AI image)**  
Using Automatic1111 StableDiffusion - ImgToImg - Inpaint (Image: Moe-Generated-LoopUpscaled-InpaintTouchup.png) - Parameters:  
Prompt: middle-aged skinny bar owner with wrinkles pointing a (wood shotgun:1.2) at the viewer, curly grey hair, wearing shirt, hyperrealism, realistic, hyperdetailed, digital painting, bar background  
Negative prompt: EasyNegative, (bad_prompt:0.8), text, watermark, glasses, bald, facial hair, muscular, hat, woman, scope, gun scope, mustache, beard  
Steps: 34, Sampler: DDIM, CFG scale: 8, Seed: 2123144937, Size: 5056x3392, Model hash: 4199bcdd14, Model: revAnimated_v122, Denoising strength: 0.2, Ultimate SD upscale upscaler: 4x-UltraSharp, Ultimate SD upscale tile_width: 512, Ultimate SD upscale tile_height: 512, Ultimate SD upscale mask_blur: 8, Ultimate SD upscale padding: 32, ControlNet: "preprocessor: tile_resample, model: control_v11f1e_sd15_tile [a371b31b], weight: 1, starting/ending: (0, 1), resize mode: Crop and Resize, pixel perfect: False, control mode: Balanced, preprocessor params: (64, 1, 64)"  
Result - New Image: 5056x3392 resolution, Ultimate SD Upscaler brings out more detail & increases reolution to 4K+, ControlNet Tiling allows for very large image size without running out of GPU memory  
![Moe Generated-4KPlus](https://github.com/bartczernicki/StableDiffusion/blob/main/ImgToImg/Simpsons/Moe/Moe-Generated-4KPlus.jpg)

Required Components
1) Automatic1111 Stable Diffusion UI: https://github.com/AUTOMATIC1111/stable-diffusion-webui  
2) ControlNet: https://github.com/lllyasviel/ControlNet  
3) ReVAnimated Stable Diffusion AI Model: https://civitai.com/models/7371?modelVersionId=46846  
4) Loopback Scaler (Python Script for improving image quality): https://github.com/Elldreth/loopback_scaler  
5) EasyNegative (Negative Embeddings): https://civitai.com/models/7808/easynegative  
6) BadPrompt (Negative Embeddings): https://civitai.com/models/55700/badprompt-negative-embedding  
