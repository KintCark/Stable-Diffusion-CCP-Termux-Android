# Stable-Diffusion-CCP-Termux-Android
I've Made An Easy to Follow install Guide For Sd.ccp its uses way less ram than fastsdcpu and u can use any model and lora or vae it supports sd14,sd15,sdxl,and sd3 

Before installing virtual environment
make sure u install ubuntu in termux first 


Looks like Python 3.12 actually Works!! U have to create a virtual environment so here is the guide:


To run sdcpp in a separate environment on Termux with Python 3.10.11, follow these steps:


---

1. Install Required Packages

First, ensure your Termux is updated and install necessary packages:

apt update -y && apt upgrade -y
apt install python3-full git ffmpeg


---

2. Install & Setup a Virtual Environment

Create and activate a virtual environment:

python3 -m venv sdcpp-env
source sdcpp-env/bin/activate


AAAAAA YOO! you can install vulkan now it will use the android graphics for gpu acceleration 
I've updated the guide to install vulkan.



Update: Flux is now Supported 


HERES AN EASY SD
CCP INSTALL GUIDE THIS BABY RUNS WAY LESS RAM I EVEN CAN USE SDXL AND SD3!!! 
U CAN EVEN PICK AMOUNT OF THREADS YOUR CPU HAS.

you can use this to quantize any . model you want if u got limited ram just quantize the model but do note the lower you quantize the lower the quality of images you get.

Update: I currently tried to quantize aura flow 2 but I didn't have enough RAM to save the output. but it did successfully qaunt it.



1

pkg updated && pkg upgrade -y && termux-setup-storage && pkg install wget -y && pkg install git -y && pkg install proot -y && cd ~ && git clone https://github.com/MFDGaming/ubuntu-in-termux.git && cd ubuntu-in-termux && chmod +x ubuntu.sh && ./ubuntu.sh -y && ./startubuntu.sh

2

apt update && apt upgrade -y && apt-get install curl git gcc make build-essential python3 python3-dev python3-pip python3-venv python-is-python3 -y && pip install ffmpeg && apt dist-upgrade -y && apt install wget && apt-get install libgl1 libglib2.0-0 libsm6 libxrender1 libxext6 -y && apt-get install google-perftools &&
apt install libgoogle-perftools-dev && pip install moviepy==1.0.3 && pip install cmake && apt install build-essential libvulkan-dev vulkan-tools mesa-vulkan-drivers -y 


Install & Setup a Virtual Environment
Create and activate a virtual environment:

python3 -m venv sdccp-env

source sdccp-env/bin/activate




install required packages for vulkan it will take an hour depending upon your phone


git clone https://github.com/google/shaderc.git

cd shaderc

python3 utils/git-sync-deps 
cmake -S . -B build
cmake --build build
cmake --install build

after you install the vulkan libs make sure you cd out of the folder before continuing to step 3

3

git clone --recursive https://github.com/leejet/stable-diffusion.cpp

4

cd stable-diffusion.cpp

5

git pull origin master

6

git submodule init

7

git submodule update

8

mkdir build

9

cd build

10

cmake ..

11

cmake --build . --config Release

12
if this Command doesn't work go to the original respiratory and copy it from there

cmake .. -DSD_VULKAN=ON
cmake --build . --config Release


TO RUN

i used marco file manager to create the models folder in the build folder.

cd ubuntu-in-termux && ./startubuntu.sh


cd stable-diffusion.cpp && cd build


./bin/sd -m /root/stable-diffusion.cpp/build/models/portray_v10.safetensors -p "a lovely cat"









HERE IS ALL THE COMMAND ARGS YOU NEED TO RUN THE MODELS AND EVEN LORAS


usage: ./bin/sd [arguments]

arguments:
  -h, --help                         show this help message and exit                                          -M, --mode [MODEL]                 run mode (txt2img or img2img or convert, default: txt2img)               -t, --threads N                    number of threads to use during computation (default: -1)
                                     If threads <= 0, then threads will be set to the number of CPU physical cores
  -m, --model [MODEL]                path to full model                                                       --diffusion-model                  path to the standalone diffusion model
  --clip_l                           path to the clip-l text encoder
  --clip_g                           path to the clip-g text encoder
  --t5xxl                            path to the the t5xxl text encoder                                       --vae [VAE]                        path to vae        --taesd [TAESD_PATH]               path to taesd. Using Tiny AutoEncoder for fast decoding (low quality)
  --control-net [CONTROL_PATH]       path to control net model                                                --embd-dir [EMBEDDING_PATH]        path to embeddings                                                       --stacked-id-embd-dir [DIR]        path to PHOTOMAKER stacked id embeddings                                 --input-id-images-dir [DIR]        path to PHOTOMAKER input id images dir                                   --normalize-input                  normalize PHOTOMAKER input id images                                     --upscale-model [ESRGAN_PATH]      path to esrgan model. Upscale images after generate, just RealESRGAN_x4plus_anime_6B supported by now                          --upscale-repeats                  Run the ESRGAN upscaler this many times (default 1)                      --type [TYPE]                      weight type (examples: f32, f16, q4_0, q4_1, q5_0, q5_1, q8_0, q2_K, q3_K, q4_K)
                                     If not specified, the default is the type of the weight file             --lora-model-dir [DIR]             lora model directory                                                     -i, --init-img [IMAGE]             path to the input image, required by img2img                             --mask [MASK]                      path to the mask image, required by img2img with mask                    --control-image [IMAGE]            path to image condition, control net                                     -o, --output OUTPUT                path to write result image to (default: ./output.png)                    -p, --prompt [PROMPT]              the prompt to render                                                     -n, --negative-prompt PROMPT       the negative prompt (default: "")                                        --cfg-scale SCALE                  unconditional guidance scale: (default: 7.0)                             --guidance SCALE                   guidance scale for img2img (default: 3.5)                                --slg-scale SCALE                  skip layer guidance (SLG) scale, only for DiT models: (default: 0)                                          0 means disabled, a value of 2.5 is nice for sd3.5 medium                --eta SCALE                        eta in DDIM, only for DDIM and TCD: (default: 0)                         --skip-layers LAYERS               Layers to skip for SLG steps: (default: [7,8,9])                         --skip-layer-start START           SLG enabling point: (default: 0.01)                                      --skip-layer-end END               SLG disabling point: (default: 0.2)                                                                         SLG will be enabled at step int([STEPS]*[START]) and disabled at int([STEPS]*[END])                                            --strength STRENGTH                strength for noising/unnoising (default: 0.75)                           --style-ratio STYLE-RATIO          strength for keeping input identity (default: 20%)                       --control-strength STRENGTH        strength to apply Control Net (default: 0.9)                                                                1.0 corresponds to full destruction of information in init image         -H, --height H                     image height, in pixel space (default: 512)                              -W, --width W                      image width, in pixel space (default: 512)                               --sampling-method {euler, euler_a, heun, dpm2, dpm++2s_a, dpm++2m, dpm++2mv2, ipndm, ipndm_v, lcm, ddim_trailing, tcd}                                                                               sampling method (default: "euler_a")
  --steps  STEPS                     number of sample steps (default: 20)
  --rng {std_default, cuda}          RNG (default: cuda)                                                      -s SEED, --seed SEED               RNG seed (default: 42, use random seed for < 0)                          -b, --batch-count COUNT            number of images to generate                                             --schedule {discrete, karras, exponential, ays, gits} Denoiser sigma schedule (default: discrete)           --clip-skip N                      ignore last layers of CLIP network; 1 ignores none, 2 ignores one layer (default: -1)                                                                             <= 0 represents unspecified, will be 1 for SD1.x, 2 for SD2.x            --vae-tiling                       process vae in tiles to reduce memory usage
  --vae-on-cpu                       keep vae in cpu (for low vram)
  --clip-on-cpu                      keep clip in cpu (for low vram)                                          --diffusion-fa                     use flash attention in the diffusion model (for low vram)                                                   Might lower quality, since it implies converting k and v to f16.                                            This might crash if it is not supported by the backend.
  --control-net-cpu                  keep controlnet in cpu (for low vram)                                    --canny                            apply canny preprocessor (edge detection)                                --color                            Colors the logging tags according to level                               -v, --verbose


WANT TO SEE YOUR IMAGE AFTER IT GENERATES INSTALL THIS.PUT THE COMMAND AT THE END OF YOUR ARGS

pip install termvisage

COMMAND>

 && termvisage /root/stable-diffusion.cpp/build/output.png





