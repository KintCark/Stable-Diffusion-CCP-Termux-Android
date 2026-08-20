I Didn't know you Don't Need Ubuntu To Run SD.cpp it works completely Native. all those packages where not needed. 😁😅👍😎🤯




pkg update

pkg upgrade -y

pkg install git cmake python wget && pkg install libwebp &&  pkg install nodejs && npm install -g npm@12.0.1 -g pnpm

git clone --recursive https://github.com/leejet/stable-diffusion.cpp

cd stable-diffusion.cpp 

mkdir build && cd build

cmake -D SD_USE_SYSTEM_WEBP=ON .. && cmake .. -DSD_BUILD_SERVER=OFF -DSD_METAL=OFF -DSD_CUDA=OFF
make -j4


./bin/sd-cli -m ~/stable-diffusion.cpp/build/models/sd3_medium.safetensors --clip_l ~/stable-diffusion.cpp/build/models/clip_l.safetensors --clip_g ~/stable-diffusion.cpp/build/models/clip_g.safetensors --t5xxl ~/stable-diffusion.cpp/build/models/t5xxl_fp8_e4m3fn.safetensors  -H 256 -W 256 -p 'a lovely cat holding a sign says /"Stable diffusion 3.5 Large/"' -n "Incorrect anatomy, incorrectly designed, incorrect geometry, low quality, Normal quality, worst quality,  Low res, Deformed, mutated, monster, horrible, Retarded, stupid, Disobedience, ignoring Prompt, ugly, Boring, incorrect colors, Incorrect lighting, incorrect shadows, incorrect depth, incorrect text, incorrect render, Glitches, errors, Asymmetric, perfect, anime, cartoon, annoying, amateur, Disgusting, Disfigured " --cfg-scale 3.3 --offload-to-cpu --stream-layers --max-vram -1 --sampling-method euler -v --clip-on-cpu --threads 8 --clip-skip 6
