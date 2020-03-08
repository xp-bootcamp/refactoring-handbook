# Tennis Game 案例介绍 

## 业务背景
网球有一个比较奇怪的评分系统，对新手来说，跟踪一下有点困难。 网球协会已经签约你建立一个记分板来在网球比赛中显示当前得分。

你的任务是编写一个`TennisGame`类，其中包含将正确的分数输出为字符串以显示在记分板上的逻辑。 当玩家得分时，它会触发类上要调用的方法，让裁判知道谁得分了。 稍后，你将从记分板上调用一个叫 `score()`的方法，询问其应显示什么。 此方法应返回具有当前分数的字符串。

以下是从网球积分规则中总结的一些规则：

- 第一位赢得比赛的玩家赢得了至少4分，并且比对手多赢得了至少2分
- 每个游戏的得分都以网球特有的方式描述： 从零到三点的分数分别被描述为`Love`、`Fifteen`、`Thirty`和`Forty`
- 如果每个玩家至少得到了三点，且得分相等，得分为`Deuce`。
- 如果每方至少得分3分，并且玩家比对手多1分，则该游戏的得分对领先的玩家来说是`Advantage`

你任务只需要报告当前游戏的得分。


## 代码库

[Tennis-Game-1](https://github.com/xp-bootcamp/refactoring-tennis-game-1)


```sh
$ git clone https://github.com/xp-bootcamp/refactoring-tennis-game-1.git
$ cd refactoring-tennis-game-1
$ ./gradlew build
```
