# Raylib Tutorial: Textures and Sprites in CLion

## Table of Contents

1. **Loading and Displaying Textures**
2. **Manipulating Textures**
3. **Animation Basics**
4. **Vocabulary**
5. **Examples**
6. **Assignments**

---

- You can find Textures and Sprites [Here](https://github.com/raysan5/raylib/blob/master/examples/textures/textures_image_kernel.png)
- Along with Sample Code

## 1. Loading and Displaying Textures

### Overview
Textures are 2D images loaded into memory to be used in your application. Raylib provides efficient methods for loading and displaying textures on the screen.

### Key Functions
- `LoadTexture(const char *fileName)`: Loads a texture from an image file.
- `UnloadTexture(Texture2D texture)`: Frees the memory used by a texture.
- `DrawTexture(Texture2D texture, int posX, int posY, Color tint)`: Draws the texture on the screen.

### Example
```c
#include "raylib.h"

int main() {
    // Initialization
    InitWindow(800, 600, "Loading and Displaying Textures");
    Texture2D texture = LoadTexture("resources/my_texture.png");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);

        // Display the texture
        DrawTexture(texture, 100, 100, WHITE);

        EndDrawing();
    }

    // Cleanup
    UnloadTexture(texture);
    CloseWindow();

    return 0;
}
```

---

## 2. Manipulating Textures

### Overview
Manipulating textures involves resizing, rotating, or applying effects to them. Raylib includes various functions to transform textures.

### Key Functions
- `DrawTextureEx(Texture2D texture, Vector2 position, float rotation, float scale, Color tint)`: Draws a texture with rotation and scaling.
- `DrawTextureRec(Texture2D texture, Rectangle sourceRec, Vector2 position, Color tint)`: Draws a part of the texture.

### Example
```c
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Manipulating Textures");
    Texture2D texture = LoadTexture("resources/my_texture.png");

    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);

        // Draw with scaling and rotation
        DrawTextureEx(texture, (Vector2){200, 150}, 45.0f, 2.0f, WHITE);

        EndDrawing();
    }

    UnloadTexture(texture);
    CloseWindow();
    return 0;
}
```

---

## 3. Animation Basics

### Overview
Sprite animation involves cycling through different parts of a texture to create motion. Raylib allows you to easily define and display sprite frames.

### Key Functions
- `DrawTextureRec(Texture2D texture, Rectangle sourceRec, Vector2 position, Color tint)`: Draws a specified rectangle of the texture.

### Example
```c
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Animation Basics");
    Texture2D spriteSheet = LoadTexture("resources/sprite_sheet.png");

    const int frameWidth = spriteSheet.width / 4;
    const int frameHeight = spriteSheet.height;
    int currentFrame = 0;
    float frameTime = 0.1f; // Time per frame
    float elapsedTime = 0.0f;

    while (!WindowShouldClose()) {
        float deltaTime = GetFrameTime();
        elapsedTime += deltaTime;

        if (elapsedTime >= frameTime) {
            currentFrame++;
            elapsedTime = 0.0f;
        }

        currentFrame %= 4; // Reset to frame 0 after the last frame

        Rectangle sourceRec = {currentFrame * frameWidth, 0, frameWidth, frameHeight};
        Vector2 position = {400 - frameWidth / 2, 300 - frameHeight / 2};

        BeginDrawing();
        ClearBackground(RAYWHITE);

        DrawTextureRec(spriteSheet, sourceRec, position, WHITE);

        EndDrawing();
    }

    UnloadTexture(spriteSheet);
    CloseWindow();
    return 0;
}
```

---

## 4. Vocabulary

- **Texture**: A 2D image loaded into memory for rendering.
- **Sprite**: A 2D graphic used in games, often part of an animation.
- **Source Rectangle**: A section of the texture to be drawn.
- **Tint**: A color applied to the texture to modify its appearance.

---

## 5. Examples

1. Load and display a texture.
2. Scale and rotate a texture.
3. Animate a sprite using a sprite sheet.

---