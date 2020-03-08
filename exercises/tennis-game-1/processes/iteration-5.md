# Iteration 5：简化条件判断

## 封装条件判断信息

- 创建`Player.hasWonAgainst(Player)`
- 创建`Player.hasAdvantageOver(Player)`
- 创建 `Player.isTiedWith(Player)`

```java
public class Player {
    public boolean isTied(Player player) {
        return score == player.score;
    }
    public boolean hasWonAgainst(Player player) {
        return score >= 4 && score - player.score >= 2;
    }
    public boolean hasAdvantageOver(Player player) {
        return score >= 4 && score - player.score == 1;
    }
}
```

## 替换条件判断逻辑
```java
public String getScore() {
    if (player1.isTiedWith(player2)) {
        return scoreForTied();
    }
    if (player1.hasAdvantageOver(player2)) {
        return scoreForAdvantage(player1);
    }
    if (player2.hasAdvantageOver(player1)) {
        return scoreForAdvantage(player2);
    }
    if (player1.hasWonAgainst(player2)) {
        return scoreForWin(player1);
    }
    if (player2.hasWonAgainst(player1)) {
        return scoreForWin(player2);
    }
    return scoreForBothBelow4Points();
}
```
