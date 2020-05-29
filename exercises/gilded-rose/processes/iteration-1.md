## Iteration 1：移动核心逻辑

### 抽取变量

```java
Item item = item[i]；
```



### 抽取/移动方法

抽取方法`update`，移动到`Item`类



### 清理Item中的字段

rename sell_in

private item中的三个属性