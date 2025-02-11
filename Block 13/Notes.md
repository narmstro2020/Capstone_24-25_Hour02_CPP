# Raylib Tutorial: The Game Loop

## 1. Understanding the Game Loop

### Vocabulary
| Term            | Definition |
|----------------|------------|
| Game Loop      | A continuous cycle in a game that updates game logic and renders graphics. |
| FPS (Frames Per Second) | The number of frames rendered per second, affecting game smoothness. |
| Delta Time     | The time difference between frames, used for frame-independent movement. |
| Update        | The phase where game logic is processed, such as input handling and physics updates. |
| Draw          | The phase where graphics are rendered onto the screen. |

### Description
The game loop is the backbone of any real-time game. It ensures the game continuously updates its logic and refreshes the screen to provide a smooth gaming experience. The standard game loop consists of three main steps:
1. **Process Input** – Handles user input like keyboard presses or mouse movements.
2. **Update Game Logic** – Updates character positions, physics calculations, and other game state changes.
3. **Render Graphics** – Draws game elements on the screen.

In Raylib, a basic game loop follows this structure:

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Raylib Game Loop Example");
    SetTargetFPS(60);
    
    while (!WindowShouldClose()) { // Main game loop
        // Update game logic here
        
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Hello, Game Loop!", 300, 280, 20, BLACK);
        EndDrawing();
    }
    
    CloseWindow();
    return 0;
}
```

---

## 2. Frame Management

### Vocabulary
| Term                | Definition |
|--------------------|------------|
| Fixed Time Step   | A technique where updates occur at fixed intervals to ensure consistency. |
| Variable Time Step | Updates occur based on real-time intervals, useful for animations and physics. |
| V-Sync            | Synchronization with the display refresh rate to prevent screen tearing. |

### Description
Frame management ensures smooth rendering and prevents unnecessary CPU/GPU usage. Raylib provides functions like `SetTargetFPS()` to regulate frame rates. The two primary techniques for managing frame updates are:

1. **Fixed Time Step**: Useful for physics updates to ensure consistent behavior across different machines.
2. **Variable Time Step**: Updates are calculated based on real-time delta time (`GetFrameTime()`).

### Example Code for Fixed Time Step:
```cpp
const float timeStep = 1.0f / 60.0f;
float accumulator = 0.0f;

while (!WindowShouldClose()) {
    float deltaTime = GetFrameTime();
    accumulator += deltaTime;
    
    while (accumulator >= timeStep) {
        // Update logic at a fixed interval
        accumulator -= timeStep;
    }
    
    BeginDrawing();
    ClearBackground(RAYWHITE);
    DrawText("Fixed Time Step Example", 300, 280, 20, BLACK);
    EndDrawing();
}
```

### Example Code for Variable Time Step:
```cpp
while (!WindowShouldClose()) {
    float deltaTime = GetFrameTime();
    
    // Move an object based on delta time
    position.x += speed * deltaTime;
    
    BeginDrawing();
    ClearBackground(RAYWHITE);
    DrawText("Variable Time Step Example", 300, 280, 20, BLACK);
    EndDrawing();
}
```

---

## 3. Best Practices

### Vocabulary
| Term              | Definition |
|------------------|------------|
| Double Buffering | Using two buffers to prevent flickering while rendering frames. |
| Culling          | Optimizing rendering by skipping objects not visible on screen. |
| Interpolation    | Smoothing out movement when frame rates fluctuate. |

### Best Practices for a Smooth Game Loop
1. **Use `SetTargetFPS()`** – Helps maintain a consistent frame rate.
2. **Optimize Drawing Calls** – Minimize unnecessary drawing operations to improve performance.
3. **Use Double Buffering** – Raylib handles this internally via `BeginDrawing()` and `EndDrawing()`.
4. **Limit CPU Usage** – Avoid heavy computations within the loop; offload tasks to separate threads if necessary.
5. **Debug Performance with `GetFPS()`** – Monitor frame rates to detect slowdowns.

### Example of Performance Monitoring:
```cpp
while (!WindowShouldClose()) {
    BeginDrawing();
    ClearBackground(RAYWHITE);
    DrawText(TextFormat("FPS: %i", GetFPS()), 10, 10, 20, RED);
    EndDrawing();
}
```

---

## More Examples

### Example 1: Basic Game Loop
Write a simple Raylib program that initializes a window, sets a target FPS, and displays a "Game Running" message on the screen.


### Example 2: Frame Rate Display and Optimization
Write a program that continuously displays the current FPS on the screen and optimizes frame rendering by setting a target FPS.

---

## More Examples: Solutions

### Example 1: Solution: Basic Game Loop
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Basic Game Loop");
    SetTargetFPS(60);
    
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Game Running", 350, 280, 20, BLACK);
        EndDrawing();
    }
    
    CloseWindow();
    return 0;
}
```

### Example 2: Solution: Frame Rate Display and Optimization
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Frame Rate Display");
    SetTargetFPS(60);
    
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText(TextFormat("FPS: %i", GetFPS()), 10, 10, 20, RED);
        EndDrawing();
    }
    
    CloseWindow();
    return 0;
}
```