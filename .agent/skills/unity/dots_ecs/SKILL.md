---
name: unity_dots_ecs
description: Entity Component System, ISystem, IJobEntity, Burst scaling, and NativeArray manual memory. Use for high-performance entities.
---

# DOTS Rules

## ISystem (Struct-based)
```csharp
[BurstCompile]
public partial struct MySystem : ISystem {
    [BurstCompile]
    public void OnUpdate(ref SystemState state) { }
}
```

## Data Iteration (IJobEntity)
Use `partial struct` for Jobs. Use `in` for read-only and `ref` for write access.

## Memory
Use `NativeArray<T>` with appropriate `Allocator` (Temp, TempJob, Persistent).
