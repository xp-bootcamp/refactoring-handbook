## Iteration 0：测试&清理

### 构建测试

使用jUnit的参数化测试，覆盖各种种类的商品

```java
class GildedRoseTest {

    @ParameterizedTest
    @MethodSource({"provideAgedBries", "provideBackstagePasses", "provideSulfuras", "provideRegularItems"})
    void should_update_item_correctly(TestFixture testFixture) {
        Item item = createItem(testFixture.name, testFixture.sellIn, testFixture.quality);

        new GildedRose(new Item[]{item}).update_quality();

        Item expectedItem = createItem(testFixture.name, testFixture.updatedSellIn, testFixture.updatedQuality);
        assertThat(item.toString()).isEqualTo(expectedItem.toString());
    }
    ......
}
```
