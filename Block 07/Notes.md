
# Core Concepts in Raylib for C++ using CLion

This tutorial introduces the core concepts of using Raylib, a simple and easy-to-use library for learning game programming, with C++ in the CLion IDE. It includes vocabulary, detailed explanations, examples, assignments, and assignment solutions.

---

## Table of Contents
1. Introduction to Raylib and Setup in CLion
2. Window Management
3. Basic Input Handling
4. Drawing Shapes and Text
5. Working with Colors
6. Assignments and Solutions

---

## 1. Introduction to Raylib and Setup in CLion

### Vocabulary
- **Library**: A collection of prewritten code that developers can use to save time.
- **Framework**: A foundation that provides tools and guidelines for development.
- **Raylib**: A C library designed for game development.
- **IDE**: Integrated Development Environment, a software suite to facilitate development.

### Steps to Set Up Raylib in CLion
1. **Install Raylib:** Download Raylib from [raylib.com](https://www.raylib.com/) and follow the installation guide for your platform.
2. **Set Up CLion Project:**
    - Create a new CMake project.
    - Include Raylib in your `CMakeLists.txt`:
      ```cmake
      cmake_minimum_required(VERSION 3.16)
      project(RaylibExample)

      set(CMAKE_CXX_STANDARD 17)

      find_package(raylib CONFIG REQUIRED)

      add_executable(RaylibExample main.cpp)
      target_link_libraries(RaylibExample raylib)
      ```
3. **Verify Setup:** Run a sample program to ensure Raylib is correctly linked.

---

## 2. Window Management

### Vocabulary
- **Window**: The graphical display where the program runs.
- **Resolution**: The dimensions of the window in pixels.
- **FPS**: Frames per second, the rate at which the screen updates.

### Explanation
Raylib provides functions to create and manage windows. The primary functions are:
- `InitWindow()`: Initializes the window.
- `WindowShouldClose()`: Checks if the user has requested to close the window.
- `CloseWindow()`: Closes the window and releases resources.

### Example
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Window Management Example");

    SetTargetFPS(60); // Set FPS to 60

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Hello, Raylib!", 350, 280, 20, DARKGRAY);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## 3. Basic Input Handling

### Vocabulary
- **Input**: Data received from a device such as a keyboard or mouse.
- **Polling**: Checking for user input in a loop.

### Explanation
Raylib supports input handling with:
- `IsKeyPressed()`: Checks if a key is pressed.
- `IsKeyDown()`: Checks if a key is being held down.
- `GetMousePosition()`: Gets the current position of the mouse.

### Example
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Input Handling Example");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);

        if (IsKeyPressed(KEY_SPACE)) {
            DrawText("Spacebar pressed!", 300, 280, 20, DARKGREEN);
        }

        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## 4. Drawing Shapes and Text

### Vocabulary
- **Shape**: A 2D graphical element like a circle or rectangle.
- **Text Rendering**: Displaying text on the screen.

### Explanation
Raylib provides functions to draw shapes and text:
- Shapes: `DrawRectangle()`, `DrawCircle()`, etc.
- Text: `DrawText()`.

### Example
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Drawing Shapes Example");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);

        DrawRectangle(200, 150, 400, 300, SKYBLUE);
        DrawCircle(400, 300, 50, RED);
        DrawText("Shapes and Text", 310, 50, 20, DARKGRAY);

        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## 5. Working with Colors

### Vocabulary
- **Color**: Defined using RGBA (Red, Green, Blue, Alpha).
- **Alpha**: Opacity level of a color.

### Explanation
Raylib provides a predefined color palette and allows custom colors:
- Predefined: `RAYWHITE`, `SKYBLUE`, etc.
- Custom: Use `Color` structure: `{ r, g, b, a }`.

### Example
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Working with Colors");

    Color customColor = { 128, 0, 128, 255 }; // Purple

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(customColor);
        DrawText("Custom Color Background", 250, 280, 20, RAYWHITE);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## 6. Assignments and Solutions

### Assignment 1: Create a Window
- Create a window with the title "My First Raylib Window".
- Set the background to `LIGHTGRAY`.
- Display the text "Welcome to Raylib!" in the center.

#### Solution
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "My First Raylib Window");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(LIGHTGRAY);
        DrawText("Welcome to Raylib!", 310, 280, 20, DARKGRAY);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

### Assignment 2: Interactive Shapes
- Draw a rectangle that changes color when the spacebar is pressed.


