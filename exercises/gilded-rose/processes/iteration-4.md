## Iteration 4：优化更新步骤
### 优化更新Quality

```java
// from
private void updateQuality() {
  if (!isAgedBrie()
      && !isBackstagePass()) {
    if (quality > 0) {
      if (!isSulfuras()) {
        quality = quality - 1;
      }
    }
  } else {
    if (quality < 50) {
      quality = quality + 1;

      if (isBackstagePass()) {
        if (sellIn < 11) {
          increaseQuality();
        }

        if (sellIn < 6) {
          increaseQuality();
        }
      }
    }
  }
}

// to
private void updateQuality() {
  if (isAgedBrie()) {
    if (quality < 50) {
      quality = quality + 1;
    }
    return;
  }
  if (isBackstagePass()) {
    increaseQuality();
    if (sellIn < 11) {
      increaseQuality();
    }
    if (sellIn < 6) {
      increaseQuality();
    }
    return;
  }
  if (isSulfuras()) {
    return;
  }
  if (quality > 0) {
    quality = quality - 1;
  }
}
```

### 优化更新SellIn

```java
// from
private void updateSellIn() {
  if (!isSulfuras()) {
    sellIn = sellIn - 1;
  }
}

// to
private void updateSellIn() {
  if (isSulfuras()) {
    return;
  }
  sellIn = sellIn - 1;
}
```



### 优化过期后的更新

```java
// from

private void updateQualityAfterExpired() {
  if (!isAgedBrie()) {
    if (!isBackstagePass()) {
      if (quality > 0) {
        if (!isSulfuras()) {
          quality = quality - 1;
        }
      }
    } else {
      quality = 0;
    }
  } else {
    increaseQuality();
  }
}

// to
private void updateQualityAfterExpired() {
  if (isAgedBrie()) {
    increaseQuality();
    return;
  }
  if (isBackstagePass()) {
    quality = 0;
    return;
  }
  if (isSulfuras()) {
    return;
  }
  if (quality > 0) {
    quality = quality - 1;
  }
}
```