---
name: unity_testing
description: Standardized Edit/Play mode tests using the AAA pattern and NUnit Constraint model. Use when writing unit tests or integration tests.
---

# Testing Standards

## Edit Mode Tests
Tests logic independent of Unity loop. Place in `Tests/EditMode/`.

## Play Mode Tests
Tests GameObjects/Physics. Place in `Tests/PlayMode/`.

## AAA Pattern & Assert.That
```csharp
[Test]
public void Calc_Sum_ReturnsCorrect() {
    // Arrange
    int a = 2, b = 3;
    // Act
    int res = a + b;
    // Assert
    Assert.That(res, Is.EqualTo(5));
}
```
