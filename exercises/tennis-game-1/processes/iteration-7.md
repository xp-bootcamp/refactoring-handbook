# Iteration 7：封装条件表达式

从这些条件判断语句中，可以找到一定的规律，成对的可以合并在Score中提供一个恰当的函数来表示。

## 提炼方法`isApplied(Player, Player)`

在Score类中创建方法`isApplied()`，将`getScore()`中成对比较的条件表达式合并封装到Score类中，例如：

```java
public class AdvantageScore {
    private final Player player;
    private Player player2;

    public AdvantageScore(Player player1, Player player2) {
        this.player = player1;
        this.player2 = player2;
    }

    public boolean isApplied() {
        return player.hasAdvantageOver(player2) || player2.hasAdvantageOver(player);
    }

    public String state() {
        return "Advantage " + (player.hasAdvantageOver(player2) ? player.getName() : player2.getName());
    }
}
```

## 替换掉条件表达式

替换掉`getScore()`中的条件表达式：

```java
public String getScore() {
    TiedScore tiedScore = new TiedScore(player1, player2);
    if (tiedScore.isApplied()) {
        return tiedScore.state();
    }
    AdvantageScore advantageScore = new AdvantageScore(player1, player2);
    if (advantageScore.isApplied()) {
        return advantageScore.state();
    }
    WinScore winScore = new WinScore(player1, player2);
    if (winScore.isApplied()) {
        return winScore.state();
    }
    RegularLandScore regularLandScore = new RegularLandScore(player1, player2);
    if (regularLandScore.isApplied()) {
        return regularLandScore.state();
    }
    return "";
}

```
