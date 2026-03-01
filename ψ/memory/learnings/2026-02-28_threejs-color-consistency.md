# WebGL Color Consistency against Lighting

Date: 2026-02-28
Source: rrr: REPO

When working with data visualizations in Three.js, using `MeshStandardMaterial` can result in "washed out" colors because the final render pixel is influenced heavily by both `AmbientLight` and `DirectionalLight`. If the scene is set to a dark, atmospheric tone, the material will render grayish even if the base color is bright neon.

**Pattern:** 
For distinct, data-driven node coloring that must pop against dark scenes, use `MeshBasicMaterial` with `transparent: true`. It is unlit, ensuring it renders the exact hex color supplied without light distortion.
