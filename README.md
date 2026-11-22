# Bloody Good Curry

A 2D top-down hack-and-slash game on a custom C++17 engine and editor, built from scratch by a 7-person team at DigiPen (September 2025 – April 2026). I was the team's Graphics Lead.

▶️ **Play it in your browser:** https://bloodygoodcurry.netlify.app/

**Stack:** C++17 · OpenGL / GLSL · ImGui · FMOD · CMake · Emscripten (WebAssembly + WebGL 2)

> The engine source belongs to the team project and stays private. This page is the write-up of my part. I'm happy to walk through the code in an interview.

## The engine at a glance

- About 53,000 lines of C++ for the engine and editor
- Component-based game objects, with levels and prefabs saved as JSON
- Pooled allocators, and 2D physics with a grid broad phase
- One codebase ships as a Windows build and a browser build (WebAssembly)

## My part

### Rendering pipeline
I owned the render system: game and editor viewports, an orthographic camera, screen-to-world picking, procedural glow lighting and combat VFX.

### Case study: the densest level was draw-call bound
- **Problem:** the busiest level issued 250 draw calls per frame.
- **Change:** GPU-instanced sprite batching, so sprites sharing a texture draw in one call.
- **Result:** 156 draw calls per frame, a 38% cut.

### Core loop and profiling
I wrote the engine's fixed-timestep main loop and a per-frame CPU profiler with an in-game overlay, which the team used to find bottlenecks.

### Editor tools (ImGui)
Transform gizmo with undo/redo, sprite-sheet animation editor, hierarchy, inspector, JSON data editor, and layer and prefab-spawn panels.

### Game AI
Decision trees, a blackboard and a behaviour component for enemies.

## Contact

Yimo Kong · kongyimoo@gmail.com · [LinkedIn](https://www.linkedin.com/in/yimokong1224/) · [Portfolio](https://kongyimo1224.github.io/)
