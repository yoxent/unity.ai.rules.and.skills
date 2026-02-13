---
name: unity_performance_optimization
description: Memory management, native Object Pooling, Addressables optimization, and Update loop rules. Use when optimizing code or handling many objects.
---

# Performance Rules

## Native Object Pooling (Unity 6.2+)
Use `UnityEngine.Pool.ObjectPool<T>`. 
```csharp
_pool = new ObjectPool<Bullet>(
    createFunc: () => Instantiate(_prefab),
    actionOnGet: (b) => b.gameObject.SetActive(true),
    actionOnRelease: (b) => b.gameObject.SetActive(false)
);
```

## String & Collection Optimization
- Use `StringBuilder` for frequent text updates.
- Pass `StringBuilder` directly to `TMP_Text.SetText()`.

## Addressable Management
Always call `Addressables.Release(handle)` in `OnDestroy` to prevent memory leaks.
