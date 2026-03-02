# 3D Gravity Simulation (C++ / OpenGL)

A 3D gravity physics simulator written in modern C++ using OpenGL (Core Profile 3.3).

This project simulates multi-body gravitational attraction, dynamic object creation, and a deformable spacetime-inspired grid, all rendered in real time with a free-look 3D camera.

---

## Features

### Multi-Body Gravity

Objects interact using Newton’s Law of Gravitation:

F = (G * m₁ * m₂) / r²

Each body:
- Applies force to every other body
- Updates velocity and position in real time
- Responds to simple collision detection

---

### Dynamic Object Creation

- **Left Click** → Create a new object  
- **Hold Right Click** → Increase mass while initializing  
- **Release Left Click** → Launch object into simulation  

---

### Spacetime Grid Deformation

A 3D grid dynamically deforms based on mass influence.

The deformation uses a Schwarzschild-radius-inspired approximation:

rₛ = 2GM / c²

This creates a visual representation of curvature caused by massive bodies.

---

### Free-Look 3D Camera

| Control | Action |
|----------|--------|
| W / S | Move forward / backward |
| A / D | Strafe left / right |
| Space | Move up |
| Shift | Move down |
| Mouse | Look around |
| Scroll | Zoom |
| K | Pause physics |
| Q | Quit |

---

## Requirements (macOS)

This project is configured for:

- macOS
- clang++
- OpenGL 3.3 Core Profile

OpenGL is included with macOS.

### Install Dependencies (Homebrew)

```bash
brew install glfw glm
```

Libraries used:
- GLFW (window & input)
- GLM (math library)

---

## Build Instructions

### Apple Silicon (M1/M2/M3)

```bash
clang++ main.cpp -std=c++17 \
-I/opt/homebrew/include \
-L/opt/homebrew/lib \
-lglfw \
-framework OpenGL \
-framework Cocoa \
-framework IOKit \
-framework CoreVideo \
-o app
```

### Intel Mac

Replace:

```
/opt/homebrew
```

with:

```
/usr/local
```

---

## Technical Overview

### Rendering
- OpenGL 3.3 Core Profile
- Vertex + Fragment shaders
- VAO/VBO per object
- Perspective projection (GLM)

### Physics
- Pairwise gravitational force calculation
- Euler integration
- Basic collision damping

### Grid System
- Line-based 3D grid
- Updated every frame
- Vertically displaced according to mass curvature

---

## Project Structure

```
main.cpp
README.md
```

All simulation, physics, and rendering logic currently reside in a single file.

---

## Potential Improvements

- Replace Euler integration with RK4
- Barnes–Hut algorithm for O(n log n) gravity
- Proper collision merging
- Fixed timestep physics loop
- Rendering/physics separation
- GPU instancing for many-body performance
- Transition to Metal or Vulkan

---

## Purpose

This project explores:

- Orbital mechanics
- Numerical simulation
- Real-time 3D rendering
- Visual representations of relativistic effects
- Low-level graphics programming

Built as a deeper exploration into physics engines and GPU pipelines.

---

## License

MIT License (or your preferred license)
