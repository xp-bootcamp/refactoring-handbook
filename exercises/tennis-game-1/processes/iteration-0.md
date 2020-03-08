# Iteration 0：测试&清理

## 构建测试
使用jUnit5参数化测试

```java
@ParameterizedTest
@MethodSource({"provideScores"})
public void should_check_all_scores_correctly(TestFixture testFixture) {
    TennisGame tennisGame = new TennisGameImpl(player1Name, player2Name);

    int highestScore = Math.max(testFixture.player1Score, testFixture.player2Score);
    for (int i = 0; i < highestScore; i++) {
        if (i < testFixture.player1Score)
            tennisGame.wonPoint(player1Name);
        if (i < testFixture.player2Score)
            tennisGame.wonPoint(player2Name);
    }
    assertThat(tennisGame.getScore()).isEqualTo(testFixture.statement);
}
```

## 简单清理

### 重命名字段

```java
// From
private int m_score1 = 0;
private int m_score2 = 0;


// To
private int player1Score = 0;
private int player2Score = 0;
```


### 修理if语句
为单行if语句添加花括号，并替换掉Hard Code

```java
if (minusResult == 1) {
    score = "Advantage " + player1Name;
} else if (minusResult == -1) {
    score = "Advantage " + player2Name;
} else if (minusResult >= 2) {
    score = "Win for " + player1Name;
} else {
    score = "Win for " + player2Name;
}
```



