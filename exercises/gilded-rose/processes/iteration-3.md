## Iteration 3：分解更新步骤

### 分成三个阶段

```java
void update() {
  updateQuality();

  updateSellIn();

  if (isExpired()) {
    updateQualityAfterExpired();
  }
}
```

