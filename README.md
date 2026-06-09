# GPU Image Convolution

GPU-accelerated image convolution filters implemented in CUDA and C++. Each filter runs its convolution kernel on the GPU for fast parallel processing across image pixels.

## Demo

[Watch our project presentation](https://drive.google.com/file/d/1P60Z0TMibsXZlVn6mx62E7a3GYvt177k/view?usp=sharing)

## Filters

- **Sharpen** – enhances edges and fine detail
- **Emboss** – gives the image a raised, engraved look
- **Gaussian** – smooths and blurs the image
- **Sobel** – detects edges by computing intensity gradients

Each filter lives in its own folder (`Sharpen_filter/`, `emboss/`, `gaussian/`, `sobel/`).

## Requirements

- An NVIDIA GPU with CUDA support
- The CUDA Toolkit (`nvcc`)
- A C/C++ compiler

## Build & Run

Move into the folder for the filter you want and compile the source with `nvcc`:

```bash
cd gaussian
nvcc -o gaussian main.cu
./gaussian input.png output.png
```

Adjust the source file name and arguments to match the files inside each folder.

## How It Works

Image convolution slides a small kernel (matrix) over every pixel and computes a weighted sum of that pixel and its neighbors. Because each output pixel can be calculated independently, the work maps naturally onto the GPU, where thousands of threads process pixels in parallel.
