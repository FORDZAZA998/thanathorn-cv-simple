# Lesson: Three.js Material Selection for Data Visualization

Date: 2026-02-28
Source: rrr: REPO

When visualizing critical data via color (such as Air Quality Index mapped to hex codes) in a 3D scene, using `THREE.MeshStandardMaterial` can lead to "washed out" or grayish colors if the scene's ambient or directional lighting is low. The material's color interacts with the light, skewing the final pixel output.

**Solution:**
For pure data nodes that must maintain their exact hex color regardless of environmental lighting, switch to `THREE.MeshBasicMaterial`. This material is unlit and will render the exact color assigned to it, ensuring that vibrant, distinct neon colors (like Crimson for hazardous PM2.5) always pop against a dark background.
