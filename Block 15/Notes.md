# Raylib C++ Tutorial: 3D Basics

## Table of Contents
1. Introduction to 3D in Raylib
2. Setting up a 3D Scene
3. Loading and Manipulating 3D Models
4. Cameras and Projections
5. Basic Lighting
6. Resources for 3D Models
7. Assignments
8. Assignment Solutions

---

## 1. Introduction to 3D in Raylib
Raylib is a simple and powerful C library for game development that supports 2D and 3D graphics. In this tutorial, we will focus on 3D development using Raylib with C++.

### Vocabulary
| Term | Definition |
|------|------------|
| 3D Rendering | The process of generating a 2D image from a 3D model using projection and lighting techniques. |
| Mesh | A collection of vertices, edges, and faces that define the shape of a 3D object. |
| Texture | An image applied to the surface of a 3D model to give it detail. |
| Camera | A virtual viewpoint in 3D space used to view objects. |
| Projection | The method used to transform 3D coordinates into 2D screen coordinates. |

---

## 2. Setting up a 3D Scene
A basic 3D scene in Raylib requires initialization of the window, setting up the camera, and defining objects.

### Example Code
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Raylib 3D Scene");
    Camera camera = { 0 };
    camera.position = { 0.0f, 2.0f, 6.0f }; 
    camera.target = { 0.0f, 0.0f, 0.0f }; 
    camera.up = { 0.0f, 1.0f, 0.0f }; 
    camera.fovy = 45.0f;
    camera.type = CAMERA_PERSPECTIVE;
    
    SetTargetFPS(60);
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        BeginMode3D(camera);
        DrawGrid(10, 1.0f);
        EndMode3D();
        DrawText("Basic 3D Scene", 10, 10, 20, DARKGRAY);
        EndDrawing();
    }
    CloseWindow();
    return 0;
}
```

---

## 3. Loading and Manipulating 3D Models
Raylib allows you to load `.obj` and `.gltf` 3D models and apply transformations.

### Example Code
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "3D Model Loading");
    Camera camera = { 0 };
    camera.position = { 5.0f, 5.0f, 5.0f };
    camera.target = { 0.0f, 0.0f, 0.0f };
    camera.up = { 0.0f, 1.0f, 0.0f };
    camera.fovy = 45.0f;
    camera.type = CAMERA_PERSPECTIVE;

    Model model = LoadModel("resources/model.obj");
    Texture2D texture = LoadTexture("resources/texture.png");
    model.materials[0].maps[MATERIAL_MAP_DIFFUSE].texture = texture;

    Vector3 position = { 0.0f, 0.0f, 0.0f };

    SetTargetFPS(60);
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        BeginMode3D(camera);
        DrawModel(model, position, 1.0f, WHITE);
        EndMode3D();
        DrawText("3D Model Example", 10, 10, 20, DARKGRAY);
        EndDrawing();
    }
    UnloadModel(model);
    UnloadTexture(texture);
    CloseWindow();
    return 0;
}
```

---

## 4. Cameras and Projections
Raylib supports multiple camera projections: **perspective** and **orthographic**.

| Camera Type | Description |
|------------|------------|
| CAMERA_PERSPECTIVE | Mimics real-world depth perception. |
| CAMERA_ORTHOGRAPHIC | Projects objects without perspective distortion. |

### Example Code for Camera Movement
```cpp
UpdateCamera(&camera, CAMERA_FREE); // Moves camera with keyboard/mouse
```

---

## 5. Basic Lighting
Raylib provides a simple lighting system using shaders.

### Example Code
```cpp
Light light = CreateLight(LIGHT_DIRECTIONAL, (Vector3){ 50, 50, 50 }, WHITE, shader);
```

---

## 6. Resources for 3D Models
You can find free 3D models at:
- [Sketchfab](https://sketchfab.com)
- [Turbosquid](https://www.turbosquid.com)
- [CGTrader](https://www.cgtrader.com)

---

## 7. Assignments
### Assignment 1: Create a 3D Cube Rotation
Modify a basic cube model to rotate continuously using `DrawCube()`.

### Assignment 2: Load a 3D Model and Apply Textures
Load a 3D model and apply a texture of your choice.

### Assignment 3: Implement Camera Controls
Implement user-controlled camera movement with keyboard inputs.

---

## 8. Assignment Solutions
### Solution 1: Cube Rotation
```cpp
float rotation = 0.0f;
rotation += 1.0f;
DrawCube((Vector3){ 0.0f, 1.0f, 0.0f }, 2.0f, 2.0f, 2.0f, RED);
DrawCubeWires((Vector3){ 0.0f, 1.0f, 0.0f }, 2.0f, 2.0f, 2.0f, BLACK);
```

### Solution 2: Load 3D Model
```cpp
Model model = LoadModel("resources/model.obj");
Texture2D texture = LoadTexture("resources/texture.png");
model.materials[0].maps[MATERIAL_MAP_DIFFUSE].texture = texture;
```

### Solution 3: Camera Controls
```cpp
UpdateCamera(&camera, CAMERA_FIRST_PERSON);
```
