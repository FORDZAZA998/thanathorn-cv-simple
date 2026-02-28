# KlakMath Quick Reference

## What it does
An extension library for the `Unity.Mathematics` package. It adds stateless tweening (Critical Damping and Exponential), 1D gradient noise, fast hashing (`XXHash`), and rotation utilities.

## Installation
Install via Unity Package Manager using Keijiro's scoped registry:
`jp.keijiro.klak.math`

## How to use Tweening
Instead of Coroutines, keep track of state in your class (Update loop):

```csharp
using Klak.Math;
using Unity.Mathematics;

float3 _position;
float3 _velocity;

void Update() {
    float3 targetPosition = math.float3(0, 5, 0);
    // Use CdsTween to step forward smoothly using critical damping
    (_position, _velocity) = CdsTween.Step((_position, _velocity), targetPosition, 10f);
    transform.position = _position;
}
```

## How to use Noise
Noise functions are purely static and take a seed. They return values usually between -1 and 1.
```csharp
// Get 3D noise float value 
float3 randomDisplacement = Noise.Float3(math.float3(time, time, time), 12345);

// Get Fractal Noise (multiple octaves)
float fractalVal = Noise.Fractal(time, octave: 4, seed: 99);
```
