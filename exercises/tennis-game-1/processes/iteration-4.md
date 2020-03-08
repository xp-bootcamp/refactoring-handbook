# Iteration 4：封装选手信息

## 创建`Player`类并替换

替换掉`TennisGameImpl`中的选手相关的信息

```java
public class Player {
    private final String name;
    private int score;

    public Player(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public int getScore() {
        return score;
    }

    public void wonPoint() {
        score++;
    }
}

```

## 更改函数签名
- Change `scoreForAdvantage(String)` to `scoreForAdvantage(Player)`
- Change `scoreForWin(String)` to `scoreForWin(Player)`
