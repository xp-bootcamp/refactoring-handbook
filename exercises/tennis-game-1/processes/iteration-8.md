# Iteration 8：提炼抽象基类

## 提炼基类
创建一个抽象的基类 `AbstractScore`，并将字段player1、player2移到基类

```java
public abstract class AbstractScore {
    protected final Player player1;
    protected final Player player2;

    public AbstractScore(Player player1, Player player2) {
        this.player1 = player1;
        this.player2 = player2;
    }
    public abstract boolean isApplied();
    public abstract String state();
}
```

## 移动方法到超类
- 将`getScoreName(int)`变更为`static`
- 将`getScoreName(int)`移到`AbstractScore`
- 替换另个一处重复的逻辑

```java
public abstract class AbstractScore {
    static String getScoreName(int score) {
        return Arrays.asList("Love", "Fifteen", "Thirty", "Forty").get(score);
    }
}
```

重构后，`getScore()`方法变更为：

```java
public String getScore() {
    AbstractScore tiedScore = new TiedScore(player1, player2);
    if (tiedScore.isApplied()) {
        return tiedScore.state();
    }
    AbstractScore advantageScore = new AdvantageScore(player1, player2);
    if (advantageScore.isApplied()) {
        return advantageScore.state();
    }
    AbstractScore winScore = new WinScore(player1, player2);
    if (winScore.isApplied()) {
        return winScore.state();
    }
    AbstractScore regularLandScore = new RegularLandScore(player1, player2);
    if (regularLandScore.isApplied()) {
        return regularLandScore.state();
    }
    return "";
}
```