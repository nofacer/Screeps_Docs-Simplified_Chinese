原文链接：<https://docs.screeps.com/introduction.html>

> 原创翻译，未经允许禁止转载。

# 介绍

## Screeps是什么样的游戏

Screeps是一款MMORTS（大型多人在线即时战略游戏）。游戏里有很多世界，在每一个世界中，玩家可在该世界创建自己的领地。在领地上可以采集资源，建造单位以及占领别人的领土。随着你征服的领土越来越多，势力范围越来越大，你在游戏世界中的影响力也越来越大。不过荣耀与风险并存，你的领地也同时被虎视眈眈的其他玩家盯着在。

Screeps主要是为了有编程背景的人设计的。和其他RTS游戏不同的地方在于，只要你为你的单位（Creep）敲好了代码，就可以让它们自动运行，不用你亲自操作。同时和其他MMO游戏不同之处在于你不用花费成片成片的时间去玩，只用没事的时候抽空看一看一切是否进展顺利。

## 游戏世界

Screeps的游戏世界由很多相互连接的房间组成。每个房间是一个$50 \times 50 $封闭空间，可能有1～4个出口通向其他的房间。世界里的房间数量是有限的，但是会随着玩家的增加而增加。

![](https://docs.screeps.com/img/world-map.png)

[下载完整图像](http://static.screeps.com/map.png)（$9100 \times 9100$ PNG, 17.7MB）

每个房间的布局是独一无二的，由程序生成，包括以下三种元素：

* 平原（Plain Land）- 普通的地面，移动成本为2。
* 沼泽（Swamps）- 移动成本为10.
* 墙（Walls）- 阻止单位移动。

可以通过以下设施改变房间布局：

* 道路（Roads）- 可以将移动成本减小到1。随着使用道路会损坏，需要维修。
* 建筑墙壁（Constructed Walls）- 由玩家建造出的墙壁。不像天然墙壁那样，建筑墙壁可以被其他玩家攻击、破坏。
* 城墙（Ramparts）- 防御工事。自己的单位可以在城墙内移动并且在城墙被破坏之前不会被攻击。城墙会随着游戏时间推进而损坏，需要维修。

在游戏开始的时候，你可以从世界中随意选择空闲的房间作为自己的领土。之后会有一个安全期，别人没法攻击你。最好利用这段时间加强自己的防御，否则时间一过别人就可以蹂躏你。

## 殖民地（Colony）

![](https://docs.screeps.com/img/colony-center.png)

能量源（Energy Sources）是游戏里的主要资源。 可以由creeps采集。能量源的储量有限，不过会在每300个游戏计时周期恢复。

母巢（Spawn）是Colony的核心部分。可以存储采集到的能量并用能量建造新的Creep。每个房间Spawn最大的数量为3个。

Spawn本身只能构建基本单位，如果想构造高等单位就需要建造Spawn扩展设施。将在下一篇文章中介绍。

![](<https://raw.githubusercontent.com/nofacer/pic_bed/master/my_blog/footer.jpg>)
