## Iteration 10： 清理各个Ttem

- 移除is..方法
- 消除重复，提炼descreaseQuality方法
- 提炼isExpired方法，上移方法，并替代子类逻辑
- 消除子类`updateQualityAfterExpired`中的判断