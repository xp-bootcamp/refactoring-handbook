## Iteration 5： 引入多态

### 创建Aged Brie商品子类

创建商品子类`AgedBrie`，并依次覆盖三个步骤，将属于`AgedBrie`的逻辑从父类下移：

```java
public class AgedBrie extends Item {
    public AgedBrie(int sellIn, int quality) {
        super("Aged Brie", sellIn, quality);
    }

    public void updateQualityAfterExpired() {
        if (sellIn < 0) {
            increaseQuality();
        }
    }

    public void updateSellIn() {
        sellIn = sellIn - 1;
    }

    public void updateQuality() {
        increaseQuality();
    }
}
```



#### 修改测试类

修改测试类，使之引用`AgedBrid`

```java
// from
private static Item createItem(String name, int sellIn, int quality) {
  return new Item(name, sellIn, quality);
}

// to
private static Item createItem(String name, int sellIn, int quality) {
  if (name.equals("Aged Brie")) {
    return new AgedBrie(sellIn, quality);
  }
  return new Item(name, sellIn, quality);
}
```



### 移除父类关于AgedBrie的逻辑

```java
// remove
private boolean isAgedBrie() {
  return name.equals("Aged Brie");
}
```





