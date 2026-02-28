# Lesson Learned: Procedural Clearance in Three.js

**Date**: 2026-02-28
**Topic**: Three.js, Procedural Terrain, Distances

When generating random objects (like trees) or modifying a `PlaneGeometry` terrain height over a defined path (like a train track), calculating the simple distance from generation coordinates to the curve geometry is an incredibly powerful technique. 

Instead of trying to manually "flatten" areas of a grid, you can use the CatmullRomCurve3 (representing the track) and evaluate the distance from any `x, z` coordinate on your terrain to the nearest points on that curve.
If `minDistToTrack` is within a given threshold (e.g., `< 14`), you can use `THREE.MathUtils.lerp` to smoothly blend the procedural height of the mountain down to the required track elevation. 

This creates organic, natural-looking valleys and clear paths that perfectly hug complex, winding curves without manual modeling.

**Concepts**: [Three.js, Procedural Generation, Terrain, Curves, Collision Avoidance]
**Source**: rrr: thanathorn-cv-v2 (3D Map Workshop)
