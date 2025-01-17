
# Setting Up RayLib in C++ Using CLion

## Table of Contents
1. Introduction to RayLib
2. Vocabulary
3. Configuring Your Development Environment
4. Installing and Setting Up RayLib
5. Creating Your First RayLib Project
6. Writing a Simple RayLib Program
7. Debugging and Testing
8. Assignments
9. Assignment Solutions

---

## 1. Introduction to RayLib
RayLib is a simple and easy-to-use C library for game programming. It provides essential tools to create graphical applications and games quickly without a steep learning curve. This tutorial will guide you through setting up RayLib in C++ using JetBrains CLion and writing your first RayLib program.

---

## 2. Vocabulary

| Term                | Definition                                                                                   |
|---------------------|-----------------------------------------------------------------------------------------------|
| **RayLib**          | A C library designed for learning programming and creating games easily.                    |
| **CLion**           | An integrated development environment (IDE) from JetBrains designed for C and C++ projects. |
| **CMake**           | A build system generator used to manage the build process in a compiler-independent manner.  |
| **Library**         | A collection of precompiled routines that programs can use.                                  |
| **Environment**     | The combination of software and hardware where your application runs.                        |

---

## 3. Configuring Your Development Environment

### Prerequisites
Before setting up RayLib, ensure you have the following installed:
- **CLion IDE**: Download and install it from [JetBrains](https://www.jetbrains.com/clion/).
- **C++ Compiler**: Ensure you have GCC, Clang, or MSVC installed.
- **CMake**: Comes bundled with CLion.

### Steps to Configure
1. **Install a Compiler:**
   - On Windows: Install MinGW or Visual Studio Build Tools.
   - On macOS: Install Xcode Command Line Tools.
   - On Linux: Install `build-essential` using your package manager (e.g., `sudo apt install build-essential`).

2. **Install RayLib:**
   - **Windows:** Download the precompiled RayLib binaries from the [official website](https://www.raylib.com/).
   - **macOS/Linux:** Use a package manager (e.g., Homebrew: `brew install raylib` or APT: `sudo apt install libraylib-dev`).

3. **Set Up Environment Variables (Optional):**
   Add RayLib’s directory to your system’s PATH for easier access.

---

## 4. Installing and Setting Up RayLib

### Add RayLib to Your Project in CLion
1. **Create a New Project:**
   - Open CLion and select `New Project`.
   - Choose `C++ Executable` and select your preferred language standard (e.g., C++17).

2. **Configure CMakeLists.txt:**
   Modify the `CMakeLists.txt` file to include RayLib. Below is an example configuration:

   ```cmake
   cmake_minimum_required(VERSION 3.5)
   project(RayLibProject)

   set(CMAKE_CXX_STANDARD 17)

   # Include RayLib
   find_package(raylib REQUIRED) # Requires RayLib to be installed system-wide

   add_executable(RayLibProject main.cpp)
   target_link_libraries(RayLibProject raylib)
   ```

3. **Include RayLib Headers:**
   In your `main.cpp`, add the following:
   ```cpp
   #include <raylib.h>
   ```

4. **Build Your Project:**
   Click the build button in CLion to compile the project. Resolve any errors before proceeding.

---

## 5. Creating Your First RayLib Project

### Writing the Code
1. Replace the contents of `main.cpp` with this basic example:
   ```cpp
   #include <raylib.h>

   int main() {
       // Initialization
       const int screenWidth = 800;
       const int screenHeight = 600;
       InitWindow(screenWidth, screenHeight, "Hello RayLib");

       // Main game loop
       while (!WindowShouldClose()) {
           // Start Drawing
           BeginDrawing();
           ClearBackground(RAYWHITE);

           DrawText("Welcome to RayLib!", 190, 200, 20, LIGHTGRAY);

           EndDrawing();
       }

       // De-Initialization
       CloseWindow();

       return 0;
   }
   ```

2. **Run the Program:**
   - Click `Run` in CLion. A window will open displaying the message, "Welcome to RayLib!"

---

## 6. Writing a Simple RayLib Program

### Example: Drawing a Circle
Modify `main.cpp` to:

```cpp
#include <raylib.h>

int main() {
    InitWindow(800, 600, "Draw a Circle");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawCircle(400, 300, 50, BLUE);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

### Explanation
- `DrawCircle(400, 300, 50, BLUE)` draws a blue circle at the center of the screen with a radius of 50 pixels.

---

## 7. Debugging and Testing

### Debugging Tips
1. **Check Compiler Errors:**
   Ensure RayLib is correctly linked.
2. **Verify Paths:**
   Confirm the library paths in `CMakeLists.txt`.
3. **Use CLion’s Debugger:**
   Set breakpoints to step through the code.

---

This tutorial provides a comprehensive guide to setting up RayLib in CLion and includes examples to get you started on game programming. Happy coding!
