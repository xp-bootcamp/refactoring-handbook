# Iteration 2：简化条件嵌套

## 使用卫语句降低嵌套复杂度：

```java
public String getScore() {
    if (player1Score == player2Score) {
        return player1Score > 2 ? "Deuce" : getScoreName(player1Score) + "-All";
    }
    if (player1Score >= 4 || player2Score >= 4) {
        int minusResult = player1Score - player2Score;
        if (minusResult == 1) {
            return "Advantage " + player1Name;
        }
        if (minusResult == -1) {
            return "Advantage " + player2Name;
        }
        if (minusResult >= 2) {
            return "Win for " + player1Name;
        }
        return "Win for " + player2Name;
    }
    return getScoreName(player1Score) + "-" + getScoreName(player2Score);
}
```
## 提炼方法消除重复
很快注意到了这个简单明显的重复，提炼方法来消除：

```java
private String scoreForWin(String playerName) {
    return "Win for " + playerName;
}

private String scoreForAdvantage(String playerName) {
    return "Advantage " + playerName;
}
```

### 使用查询方法取代条件判断：
- Extract `isTied()` Method
- Extract `isAtLeastOneScoreAbove4Points` Method

- Extract `doesPlayer1HaveAdvantage()` method
- Extract `doesPlayer2HasAdvantage()` method
- Extract `doesPlayer1Win()` method
- Extract `doesPlayer2Win()` method


### 将三个分支处理逻辑提取到单独的函数中

- Extract `scoreForTied()` Method
- Extract `scoreForAtLeastOneScoreAbove4Points()` Method
- Extract `scoreForBothBelow4Points()` Method


```java
public String getScore() {
    if (isTied()) {
        return scoreForTied();
    }
    if (isAtLeastOneScoreAbove4Points()) {
        return scoreForAtLeastOneScoreAbove4Points();
    }
    return scoreForBothBelow4Points();
}

private String scoreForBothBelow4Points() {
    return getScoreName(player1Score) + "-" + getScoreName(player2Score);
}

private String scoreForAtLeastOneScoreAbove4Points() {
    if (doesPlayer1HaveAdvantage()) {
        return scoreForAdvantage(player1Name);
    }
    if (doesPlayer2HasAdvantage()) {
        return scoreForAdvantage(player2Name);
    }
    if (doesPlayer1Win()) {
        return scoreForWin(player1Name);
    }
    if (doesPlayer2Win()) {
        return scoreForWin(player2Name);
    }
    return "";
}

private String scoreForTied() {
    return player1Score > 2 ? "Deuce" : getScoreName(player1Score) + "-All";
}

```
