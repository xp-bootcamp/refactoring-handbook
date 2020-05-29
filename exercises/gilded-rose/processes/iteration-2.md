## Iteration 2：提炼查询方法

### 提炼查询方法

提炼3个判断Item类型的查询方法

```java
private boolean isAgedBrie() {
  return name.equals("Aged Brie");
}

private boolean isBackstagePass() {
  return name.equals("Backstage passes to a TAFKAL80ETC concert");
}

private boolean isSulfuras() {
  return name.equals("Sulfuras, Hand of Ragnaros");
}
```



提炼`increaseQuality`方法

```java
private void increaseQuality() {
  if (quality < 50) {
    quality = quality + 1;
  }
}
```

