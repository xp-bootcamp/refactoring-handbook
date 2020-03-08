# Iteration 10：消除重复

## 提炼函数
提炼`generatePossibleScores`方法，返回一个List，遍历展示：

```java
public String getScore() {
    for (AbstractScore score : generatePossibleScores()) {
        if (score.isApplied()) {
            return score.state();
        }
    }
    return new EmptyScore(player1, player2).state();
}

public List<AbstractScore> generatePossibleScores() {
    return Arrays.asList(
            new TiedScore(player1, player2),
            new AdvantageScore(player1, player2),
            new WinScore(player1, player2),
            new RegularLandScore(player1, player2)
    );
}

```


## 用Stream替换循环语句

```java
public String getScore() {
    return generatePossibleScores().stream().filter(AbstractScore::isApplied)
            .findFirst().orElse(new EmptyScore(player1, player2)).state();
}
```



