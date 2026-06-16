# RedNoise

A C++ 3D graphics rendering engine that implements both rasterization and ray tracing techniques for rendering textured 3D models with camera controls and real-time manipulation.

## Overview

RedNoise is a coursework project demonstrating computer graphics fundamentals including 3D transformations, rasterization, ray tracing, and real-time rendering. The project uses SDL2 for window management and GLM for mathematical operations.

The implementation includes:
- **Rasterization pipeline**: Rendering 3D models by projecting them onto a 2D screen
- **Ray tracing**: Realistic rendering with shadow computation and texture mapping
- **Interactive camera controls**: Real-time navigation and viewing angle manipulation
- **Texture mapping**: UV-mapped textures applied to 3D geometry

## Demo

![RedNoise Application Demo](Copy%20of%20cw_zt22740%20-%20Made%20with%20Clipchamp.gif)

The demo showcases the complete application featuring ray-traced rendering with Gouraud shading, interactive camera controls, real-time model manipulation, and texture mapping.

## Features

### Graphics Rendering
- **Rasterized rendering**: Fast, screen-space triangle rasterization with depth buffering
- **Ray-traced rendering**: Photorealistic rendering with ray-surface intersection tests
- **Texture mapping**: Support for PPM texture files with proper UV coordinate interpolation
- **Gouraud shading**: Smooth lighting using vertex normal interpolation
- **Depth buffering**: Correct handling of occlusion and depth ordering

### Interactive Features
- **Real-time camera control**: Move and rotate camera with keyboard input
- **Model orbit visualization**: Rotate around loaded 3D models
- **Screenshot capture**: Save rendered frames as BMP and PPM files
- **Random shapes**: Generate and draw random triangles for testing

## Project Structure

```
CGCW/
├── CMakeLists.txt           # Build configuration
├── Makefile                 # Alternative build system
├── src/
│   └── RedNoise.cpp         # Main application entry point
├── libs/
│   ├── sdw/                 # Graphics library (CanvasTriangle, DrawingWindow, etc.)
│   └── glm-0.9.7.2/         # Mathematics library (vectors, matrices)
├── models/
│   ├── cornell-box.obj      # Test model (wireframe)
│   ├── cornell-box.mtl      # Materials for wireframe model
│   ├── textured-cornell-box.obj    # Test model with textures
│   └── textured-cornell-box.mtl    # Materials for textured model
├── build/                   # Build output directory (generated)
├── output.bmp               # Example output (bitmap format)
├── output.ppm               # Example output (PPM format)
└── texture.ppm              # Sample texture asset
```

## Build Instructions

### Prerequisites

- **Compiler**: GCC, Clang, or MSVC (C++14 or later)
- **CMake**: Version 3.12 or higher
- **SDL2**: Development libraries and headers
  - Ubuntu/Debian: `sudo apt-get install libsdl2-dev`
  - macOS: `brew install sdl2`
  - Windows: Download from https://github.com/libsdl-org/SDL/releases

### CMake Build (Recommended)

**Step 1: Generate build files**

```bash
cmake -Bbuild -H. -DCMAKE_BUILD_TYPE=Release
```

- Replace `Release` with `Debug` for debugging builds (includes gdb and address sanitizer)
- The `-H.` specifies the source directory (current directory)
- The `-Bbuild` specifies the build directory

**Step 2: Compile**

```bash
cmake --build build --target RedNoise --config Release
```

For parallel builds on Unix-like systems:

```bash
cmake --build build --target RedNoise --config Release -- -j$(nproc)
```

The executable will be created at `build/RedNoise`.

### Make Build (Alternative)

```bash
make
```

The executable will be created as `RedNoise`.

## Usage

### Running the Application

```bash
./build/RedNoise
```

The window will display the ray-traced Cornell box model with real-time rendering.

### Output Files

The application automatically generates rendering output:
- `output.bmp` - Bitmap format output (captured on mouse click)
- `output.ppm` - Portable Pixmap format output (captured on mouse click)

## Controls

The application supports keyboard controls for real-time camera manipulation:

### Camera Movement

| Key | Action |
|-----|--------|
| `LEFT` | Move camera right (+X) |
| `RIGHT` | Move camera left (-X) |
| `UP` | Move camera up (-Y) |
| `DOWN` | Move camera down (+Y) |
| `F` | Move camera forward (-Z) |
| `B` | Move camera backward (+Z) |

### Camera Rotation

| Key | Action |
|-----|--------|
| `I` | Pitch up (rotate around X-axis) |
| `K` | Pitch down (rotate around X-axis) |
| `J` | Yaw left (rotate around Y-axis) |
| `L` | Yaw right (rotate around Y-axis) |

### Other Controls

| Key | Action |
|-----|--------|
| `U` | Draw random triangle |
| `MOUSE CLICK` | Save current frame as output.bmp and output.ppm |

---

**Developed as a Computer Graphics Coursework (CGCW) project**
