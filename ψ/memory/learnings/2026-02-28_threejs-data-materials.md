# Lesson: Three.js Material Selection for Data Integrity

Date: 2026-02-28
Source: rrr: REPO

When critical data visualization relies on specific color thresholds (e.g., Air Quality Index PM2.5 colors), the choice of Three.js material is critical. Using `THREE.MeshStandardMaterial` in a dark or atmospheric scene is dangerous because the scene's `AmbientLight` and `DirectionalLight` will heavily skew, dull, or wash out the base color, leading to inaccurate data representation.

**Solution:**
Always use `THREE.MeshBasicMaterial` for data-driven 3D nodes that require exact hex color matching. Since `MeshBasicMaterial` is unlit, it ignores scene lighting entirely and renders the pure desired color, ensuring high-contrast, vibrant UI elements against atmospheric backgrounds.
