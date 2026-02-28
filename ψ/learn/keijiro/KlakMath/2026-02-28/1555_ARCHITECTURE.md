# KlakMath Architecture

**Source:** `Packages/jp.keijiro.klak.math/Runtime`
**Namespace:** `Klak.Math`

## Core Organization
KlakMath is designed as a focused extension library for `Unity.Mathematics`. It eschews Object-Oriented paradigms (no inheritance, no MonoBehaviour dependencies) in favor of static, pure functional utility classes using the `Unity.Mathematics` types (`float2`, `float3`, `quaternion`, etc.).

## Key Abstractions

### 1. Tweening (`CdsTween.cs`, `ExpTween.cs`)
- **Philosophy:** Stateless interpolation functions. Instead of managing internal states or coroutines, the `Step` functions take the current state (value `x` and velocity `v`), target, speed, and delta time mapping mathematically to the next frame.
- **Support:** Full support for `float`, `float2`, `float3`, `float4`, and `quaternion`.

### 2. Gradient Noise (`Noise.cs`)
- **Philosophy:** Math-based procedural 1D gradient noise function, built on top of the custom `XXHash` implementation for speed.
- **Variations:** Includes standard scalar/vector noise (`Float`, `Float2`...) and Fractal Noise with multiple octaves (`Fractal`, `Fractal2`...).

### 3. Fast Hashing (`XXHash.cs`)
- **Philosophy:** A high-performance hashing implementation usable as a PRNG (Pseudo-Random Number Generator). Uses bitwise operations directly on integers mapping to normalized floats.

## Dependency Structure
- **External:** `Unity.Mathematics`. The library is firmly rooted in Unity's new ECS-friendly Mathematics stack.
- **Internal:** `Noise` depends directly on `XXHash`.
