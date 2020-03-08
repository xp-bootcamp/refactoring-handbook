# Iteration 3：合并条件表达式

## 内联方法

将`scoreForAtLeastOneScoreAbove4Points`内联回去

```java
public String getScore() {
    if (isTied()) {
        return scoreForTied();
    }
    if (isAtLeastOneScoreAbove4Points()) {
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
    return scoreForBothBelow4Points();
}
```

## 合并条件表达式
合并条件表达式，让抽象层次回归到同一层次

```java
public String getScore() {
    if (isTied()) {
        return scoreForTied();
    }
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
    return scoreForBothBelow4Points();
}

private boolean doesPlayer2Win() {
    return isAtLeastOneScoreAbove4Points() && player2Score - player1Score >= 2;
}
private boolean doesPlayer1Win() {
    return isAtLeastOneScoreAbove4Points() && player1Score - player2Score >= 2;
}
private boolean doesPlayer2HasAdvantage() {
    return isAtLeastOneScoreAbove4Points() && player1Score - player2Score == -1;
}
private boolean doesPlayer1HaveAdvantage() {
    return isAtLeastOneScoreAbove4Points() && player1Score - player2Score == 1;
}
```
