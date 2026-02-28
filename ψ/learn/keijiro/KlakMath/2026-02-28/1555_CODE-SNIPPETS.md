# KlakMath Code Snippets

## 1. Critically Damped Spring Interpolation (`CdsTween.cs`)
Stateless tweening that maintains velocity to create a smooth, bouncing-less damping toward a target.

```csharp
public static (float3 x, float3 v)
  Step((float3 x, float3 v) state, float3 target, float speed, float dt)
{
    var n1 = state.v - (state.x - target) * (speed * speed * dt);
    var n2 = 1 + speed * dt;
    var nv = n1 / (n2 * n2);
    return (state.x + nv * dt, nv);
}
```

## 2. Gradient Vector Noise (`Noise.cs`)
Usage of `XXHash` to generate pseudo-random gradients, which are then interpolated mathematically using standard 1D noise polynomial smoothing.

```csharp
public static float3 Float3(float3 p, uint seed)
{
    var hash = new XXHash(seed);

    var i = (uint3)((int3)p + 0x10000000);
    var x = math.frac(p);

    var x0 = x;
    x0 = 1 - x0 * x0;
    x0 = x0 * x0 * x0;

    var x1 = 1 - x;
    x1 = 1 - x1 * x1;
    x1 = x1 * x1 * x1;

    var g0 = hash.Float3(-1, 1, i);
    var g1 = hash.Float3(-1, 1, i + 1);

    var n = x0 * g0 * x + x1 * g1 * (x - 1);
    return n * 2 * 32 / 27;
}
```

## 3. Quaternion Euler Generation using Noise (`Noise.cs`)
Mapping 1D noise out to 3-dimensional Euler rotation properties.

```csharp
public static quaternion Rotation(float3 p, float3 angles, uint seed)
  => quaternion.EulerZXY(angles * Float3(p, seed));
```
