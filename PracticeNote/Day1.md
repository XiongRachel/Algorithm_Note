# 第一题 求出硬币游戏的赢家

#### 题目：

给你两个 **正** 整数 `x` 和 `y` ，分别表示价值为 75 和 10 的硬币的数目。

Alice 和 Bob 正在玩一个游戏。

每一轮中，Alice 先进行操作，Bob 后操作。

每次操作中，玩家需要拿出价值 **总和** 为 115 的硬币。

如果一名玩家无法执行此操作，那么这名玩家 **输掉** 游戏。

两名玩家都采取 **最优** 策略，请你返回游戏的赢家。



#### 思路：

- 因为先后操作 所以可以根据奇偶 来判断谁赢
- 根据操作次数判读谁赢 
  - 如果是偶数 0 2 4 6 8 
      就代表游戏开始Allice就不能操作所以 Bob赢
  - 如果是奇数反之
- 需要拿取的硬币总和为115 
  - 所以应该恰好拿1枚75 以及 4枚10的硬币

#### 解题 1 (常规While循环解题)：

```java
class Solution{
    public String losingPlayer(int x , int y){
        //初始变量用于计算游戏次数
        int count = 0;
        //while 循环如果x >= 1 y >= 4 就一直循环
        while(x >= 1 && y >= 4){
            //每次循环都是一轮游戏次数
            count++;
            //每次每个玩家都需要1枚75 和 4枚10
            //两名玩家都采取 最优 策略
            x -= 1;
            y -= 4;
        }
        //获得count 进行判断取模 谁是最后一次
        //偶数的情况是Alice输了 比如0 Alice根本没法操作
        if(count % 2 == 0){
            return "Bob";
        }
        //反之Bob输
        else{
            return "Alice"; 
        }
    }
}

```

#### 解题2（O1）：

```java
class Solution{
	public String losingPlayer(int x, int y){
	 int ops = Math.min(x, y / 4);
	 return ops % 2 == 0 ? "Bob" : Alice;
	}
}
```

