# Iteration 6：创建计分类

## 创建`AdvantageScroe`类

```java
public class AdvantageScore {
    private final Player player;

    public AdvantageScore(Player player) {
        this.player = player;
    }

    public String state() {
        return "Advantage " + player.getName();
    }
}
```

## 创建 `WinScroe` 类

```java
public class WinScore {
    private final Player player;

    public WinScore(Player player) {
        this.player = player;
    }

    public String state() {
        return "Win for " + player.getName();
    }
}
```

## 创建`TiedScroe` 

```java
public class TiedScore {
    private final Player player;

    public TiedScore(Player player) {
        this.player = player;
    }

    public String state(){
        return player.getScore() > 2 ? "Deuce" : getScoreName(player.getScore()) + "-All";
    }

    private String getScoreName(int score) {
        return Arrays.asList("Love", "Fifteen", "Thirty", "Forty").get(score);
    }
}
```

## 创建`RegularLandScore`类

```java
public class RegularLandScore {
    private final Player player1;
    private final Player player2;

    public RegularLandScore(Player player1, Player player2) {
        this.player1 = player1;
        this.player2 = player2;
    }

    public String state() {
        return getScoreName(player1.getScore()) + "-" + getScoreName(player2.getScore());
    }

    private String getScoreName(int score) {
        return Arrays.asList("Love", "Fifteen", "Thirty", "Forty").get(score);
    }
}
```


使用计分类替换掉获得计分表示的逻辑：

```java
public String getScore() {
    if (player1.isTiedWith(player2)) {
        return new TiedScore(player1).state();
    }
    if (player1.hasAdvantageOver(player2)) {
        return new AdvantageScore(player1).state();
    }
    if (player2.hasAdvantageOver(player1)) {
        return new AdvantageScore(player2).state();
    }
    if (player1.hasWonAgainst(player2)) {
        return new WinScore(player1).state();
    }
    if (player2.hasWonAgainst(player1)) {
        return new WinScore(player2).state();
    }
    return new RegularLandScore(player1, player2).state();
}

```