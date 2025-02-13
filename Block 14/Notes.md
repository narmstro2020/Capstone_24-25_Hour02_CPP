# Raylib 2D Rendering Tutorial

## 1. Drawing Primitives

### Vocabulary

| Term            | Definition |
|----------------|------------|
| Primitive | A basic geometric shape such as a line, rectangle, or circle that can be drawn on the screen. |
| Renderer | The system responsible for drawing graphics on the screen. |
| Color | A structure that defines a color using Red, Green, Blue, and Alpha (transparency) values. |
| Coordinates | The X and Y positions on the screen where an object is drawn. |
| Fill Mode | The mode that determines whether shapes are drawn as outlines or solid-filled. |

### Description
Raylib provides a set of functions to draw basic 2D shapes such as lines, rectangles, circles, and polygons. These primitives are essential for simple graphics and game development.

### Example Code

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Drawing Primitives");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);

        DrawLine(100, 100, 200, 200, RED);
        DrawCircle(400, 300, 50, BLUE);
        DrawRectangle(500, 400, 100, 50, GREEN);

        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## 2. Working with Fonts

### Vocabulary

| Term      | Definition |
|-----------|------------|
| Font | A graphical representation of text used in the application. |
| Glyph | An individual character or symbol within a font. |
| TTF | TrueType Font, a common scalable font format. |
| Rasterization | The process of converting font glyphs into pixels for rendering. |

### Description
Raylib allows rendering of text using built-in and custom fonts. You can load TrueType Fonts (TTF) to use custom text styles.

### Example Code

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Working with Fonts");
    Font customFont = LoadFont("resources/custom_font.ttf");
    
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);

        DrawText("Hello, Raylib!", 100, 100, 20, BLACK);
        DrawTextEx(customFont, "Custom Font", (Vector2){200, 200}, 40, 2, RED);

        EndDrawing();
    }

    UnloadFont(customFont);
    CloseWindow();
    return 0;
}
```

---

## 3. Camera2D and Scrolling Scenes

### Vocabulary

| Term        | Definition |
|------------|------------|
| Camera2D | A structure in Raylib that enables 2D transformations such as zooming and panning. |
| Offset | The screen position where the camera focuses. |
| Target | The world-space coordinate that the camera follows. |
| Zoom | A factor that scales the view. |

### Description
Camera2D allows movement and zooming in a 2D space. It is useful for creating scrolling scenes in games.

### Example Code

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Camera2D and Scrolling");
    Camera2D camera = {0};
    camera.target = (Vector2){400, 300};
    camera.offset = (Vector2){400, 300};
    camera.rotation = 0.0f;
    camera.zoom = 1.0f;

    while (!WindowShouldClose()) {
        if (IsKeyDown(KEY_RIGHT)) camera.target.x += 5;
        if (IsKeyDown(KEY_LEFT)) camera.target.x -= 5;
        if (IsKeyDown(KEY_UP)) camera.target.y -= 5;
        if (IsKeyDown(KEY_DOWN)) camera.target.y += 5;

        BeginDrawing();
        ClearBackground(RAYWHITE);
        BeginMode2D(camera);
        DrawRectangle(350, 250, 100, 100, RED);
        EndMode2D();
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

---

## More Examples

### 1. Create a Shape Drawing Tool
- Allow users to draw lines, rectangles, and circles using the keyboard.
- Use different colors for different shapes.

### 2. Custom Font Rendering
- Load a custom TTF font and display user-input text on the screen.
- Allow the user to change font size dynamically.
---

## More Examples Solutions

### More Examples 1: Shape Drawing Tool

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Shape Drawing Tool");
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawRectangle(200, 200, 100, 50, BLUE);
        DrawCircle(400, 300, 40, GREEN);
        DrawLine(100, 500, 300, 500, RED);
        EndDrawing();
    }
    CloseWindow();
    return 0;
}
```

### More Examples 2: Custom Font Rendering

```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Custom Font Rendering");
    Font customFont = LoadFont("resources/custom_font.ttf");
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawTextEx(customFont, "Dynamic Text", (Vector2){200, 200}, 30, 2, BLACK);
        EndDrawing();
    }
    UnloadFont(customFont);
    CloseWindow();
    return 0;
}
```
