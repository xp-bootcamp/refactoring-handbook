## Iteration 1：移动核心逻辑

### 简单清理

items属性私有化

```java
// From
class GildedRose {
    Item[] items;
}

// To
class GildedRose {
    private Item[] items;
}

```

清楚IDE提示

```java
// From
items[i].quality = items[i].quality - items[i].quality;

// To
items[i].quality = 0
```



### 抽取变量

```java
Item item = item[i]；
```



### 抽取/移动方法

抽取方法`update`，移动到`Item`类



### 清理Item中的字段

rename sell_in

private item中的三个属性