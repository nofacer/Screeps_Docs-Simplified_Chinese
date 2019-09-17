> 原始文档：https://docs.screeps.com/start-areas.html
> 原创翻译，未经允许禁止转载。

#  初始区域

## 新手区

为了让新手获得良好的开局体验，不被老玩家虐菜，我们设计了一个系统用来标记出适合新玩家的区域。新手区被标记为绿色，当你鼠标移上去也会看到`Novice Area`的标记。

![](https://docs.screeps.com/img/novice.png)

在新手区有如下规则：

*   新手区与外面的世界是隔离开的，并且有道隐形的不可摧毁的墙阻止其他玩家进入。进入新手区的唯一方法是直接把你初始的spawn放置进去。
*   只有GCL小于等于3的玩家可以从新手区开局。
*   每个玩家[占领](https://docs.screeps.com/api/#Creep.claimController)的房间数量不能超过3个。但是[预定](https://docs.screeps.com/api/#Creep.reserveController)数量不受限制。
*   激活[安全模式](https://docs.screeps.com/defense.html)没有冷却。
*   禁止使用[核弹](https://docs.screeps.com/api/#StructureNuker)。

新手区有倒计时，当其归于0则所有限制消失。那时候房间将不再呈现绿色，也没有空气墙了。你可以向外扩张，同时也得开始堤防外界的入侵。

（看上图）地图上一个sector的大小为10x10，sector是宽度为1的外墙。除了这个外墙，sector内部还有一个十字形的内墙，将整个区域划分为四个相同的区块。内墙的消失时间比外墙快，这意味着一个sector内的玩家的活动范围是由小到大的。

## 重生区域

和新手区一样比较特别的区域是重生区域。在地图上蓝色的区域就是重生区域。不过重生区域只有使用核弹的限制，只要GCL等级匹配，任何玩家均可占领此区域。

![](https://docs.screeps.com/img/chrome_2017-03-06_14-40-11.png)

## 区域生成方式

我们会不断监视新手区和重生区域的分配情况，并根据需求开辟新的区域。请注意，即使是老的区域，只要没人使用，没有人口，足够大就会有可能会被重新分配。

> 如果你不希望某个房间被转化为新手区或重生区，请记得[预定](https://docs.screeps.com/api/#Creep.reserveController)。

如果某个房间将被转化为新手或重生区域，那个房间所在的区块里的房间都会有这样的消息：

![](https://docs.screeps.com/img/chrome_2017-03-08_13-01-20.png)

你可以使用游戏的环境变量`SYSTEM_USERNAME`、`SIGN_NOVICE_AREA`以及`SIGN_RESPAWN_AREA`来通过程序定期检查自己是否有重要的房间将被转化，如果有上图那样的消息你也可以通过程序来预定房间。

