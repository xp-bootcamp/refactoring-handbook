# Iteration 1：提炼计分方法

在Iteration 1中，我们主要从简单的重构开始，看到一个根据分数生成得分的代码库，就可以开始了。

## 提炼`getScoreName`方法，并优化逻辑

```java
protected String getScoreName(int score) {
    switch (score) {
        case 0:
            return "Love";
        case 1:
            return "Fifteen";
        case 2:
            return "Thirty";
        case 3:
            return "Forty";
    }
    return "";
}

// 优化后
protected String getScoreName(int score) {
    return Arrays.asList("Love", "Fifteen", "Thirty", "Forty").get(score);
}
```

## 替换第两个分支逻辑，并优化逻辑

```java
// Before
switch (player1Score) {
    case 0:
        score = "Love-All";
        break;
    case 1:
        score = "Fifteen-All";
        break;
    case 2:
        score = "Thirty-All";
        break;
    default:
        score = "Deuce";
        break;
}

// After
score = player1Score > 2 ? "Deuce" : getScoreName(player1Score) + "-All";
```

```java
// Before
int tempScore = 0;
for (int i = 1; i < 3; i++) {
    if (i == 1) {
        tempScore = player1Score;
    } else {
        score += "-";
        tempScore = player2Score;
    }
    score += getScoreName(tempScore);
}

// After
score = getScoreName(player1Score) + "-" + getScoreName(player2Score);
```