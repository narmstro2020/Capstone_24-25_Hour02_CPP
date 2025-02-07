# C++ Raylib Audio Tutorial

Raylib is a simple and easy-to-use C library for game development, and it has built-in support for handling audio. This tutorial will cover:
- Loading and playing sounds
- Music management
- Audio effects

Each section includes vocabulary, definitions, examples, and assignments with solutions.

---

## 1. Vocabulary

| Term | Definition |
|------|-----------|
| `InitAudioDevice()` | Initializes the audio system in Raylib. |
| `CloseAudioDevice()` | Closes the audio system and frees all allocated resources. |
| `LoadSound()` | Loads a sound file into memory for short sound effects. |
| `UnloadSound()` | Frees the memory allocated for a loaded sound. |
| `PlaySound()` | Plays a loaded sound effect. |
| `StopSound()` | Stops a currently playing sound. |
| `PauseSound()` | Pauses a playing sound. |
| `ResumeSound()` | Resumes a paused sound. |
| `LoadMusicStream()` | Loads a music file for streaming playback. |
| `UnloadMusicStream()` | Frees memory allocated for a loaded music stream. |
| `PlayMusicStream()` | Begins playing a loaded music stream. |
| `UpdateMusicStream()` | Updates the music buffer and keeps the stream playing smoothly. |
| `SetMasterVolume()` | Sets the global volume for all sounds and music. |
| `SetSoundVolume()` | Sets the volume level for a specific sound effect. |
| `SetMusicVolume()` | Sets the volume level for a music stream. |

---

## 2. Initializing the Audio System

Before using any audio functions in Raylib, we need to initialize the audio system.

### Example: Initializing and Closing Audio
```cpp
#include "raylib.h"

int main() {
    // Initialize the window and audio system
    InitWindow(800, 600, "Raylib Audio Example");
    InitAudioDevice();

    // Wait for user to close the window
    while (!WindowShouldClose()) {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Audio Initialized!", 200, 300, 20, DARKGRAY);
        EndDrawing();
    }

    // Cleanup
    CloseAudioDevice();
    CloseWindow();
    return 0;
}
```
This example initializes the audio system and displays a message.

---

## 3. Loading and Playing Sounds

Sounds in Raylib are best used for short sound effects (e.g., button clicks, gunshots, or jumping in a platformer).

### Example: Playing a Sound
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Sound Example");
    InitAudioDevice();

    Sound soundEffect = LoadSound("jump.wav");  // Load a sound file

    while (!WindowShouldClose()) {
        if (IsKeyPressed(KEY_SPACE)) {
            PlaySound(soundEffect);  // Play the sound when the spacebar is pressed
        }

        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Press SPACE to play sound!", 200, 300, 20, DARKGRAY);
        EndDrawing();
    }

    UnloadSound(soundEffect);
    CloseAudioDevice();
    CloseWindow();
    return 0;
}
```

---

## 4. Managing Music

Music in Raylib is loaded as a stream, making it ideal for longer audio tracks such as background music.

### Example: Playing Background Music
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Music Example");
    InitAudioDevice();

    Music bgMusic = LoadMusicStream("background.mp3");
    PlayMusicStream(bgMusic);

    while (!WindowShouldClose()) {
        UpdateMusicStream(bgMusic);  // Update the music stream every frame

        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Playing Background Music!", 200, 300, 20, DARKGRAY);
        EndDrawing();
    }

    UnloadMusicStream(bgMusic);
    CloseAudioDevice();
    CloseWindow();
    return 0;
}
```

---

## 5. Adjusting Audio Volume

Raylib allows adjusting global and individual sound/music volume.

### Example: Adjusting Volume
```cpp
#include "raylib.h"

int main() {
    InitWindow(800, 600, "Volume Control");
    InitAudioDevice();

    Music bgMusic = LoadMusicStream("background.mp3");
    PlayMusicStream(bgMusic);
    float volume = 1.0f;

    while (!WindowShouldClose()) {
        UpdateMusicStream(bgMusic);

        if (IsKeyPressed(KEY_UP) && volume < 1.0f) volume += 0.1f;
        if (IsKeyPressed(KEY_DOWN) && volume > 0.0f) volume -= 0.1f;

        SetMusicVolume(bgMusic, volume);

        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawText("Press UP to increase volume, DOWN to decrease", 150, 250, 20, DARKGRAY);
        DrawText(TextFormat("Volume: %.1f", volume), 350, 300, 20, DARKGRAY);
        EndDrawing();
    }

    UnloadMusicStream(bgMusic);
    CloseAudioDevice();
    CloseWindow();
    return 0;
}
```

---

