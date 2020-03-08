# Iteration 9：引入特殊Score

创建一个 `EmptyScore`类，并替换`getScore()`方法中的最后一个返回语句

```java
package cn.xpbootcamp.tennis;

public class EmptyScore extends AbstractScore {
    public EmptyScore(Player player1, Player player2) {
        super(player1, player2);
    }

    @Override
    public boolean isApplied() {
        return true;
    }

    @Override
    public String state() {
        return "";
    }
}

public String getScore() {
    // ...
    return new EmptyScore(player1, player2).state();
}
```