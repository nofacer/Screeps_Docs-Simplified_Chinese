> 原文链接：<https://docs.screeps.com/control.html>
> 原创翻译，未经允许禁止转载。

# 控制

## 全局控制等级（Global Control Level）

为了扩展你在游戏世界中的疆土你需要提升的一个主要指标是Global Control Level（GCL）。GCL主要影响：

* CPU限制。在官方服务器上，每个人开局有20个CPU的限制，只能控制少量的单位。如果你是订阅（氪金）用户，每提升一个GCL等级可以多获得10个CPU资源，直到达到最大的300CPU限制。
* 控制房间数量。比如说你想要控制3个房间就需要3级的GCL。

你当前的GCL等级在[overview页面](https://screeps.com/a/#!/overview)显示。

![](https://docs.screeps.com/img/gcl-cpu.png)

## 房间控制等级

如果想要在房间里建造设施，首先需要控制这个房间。在大多数房间里都有一个特殊的装置被称为房间控制器（Room Controller）。你第一个房间里的房间控制器默认归你所有。其他的中立房间控制器可以通过带有`CLAIM`部件的creep占有，取得房间控制权。

![](https://docs.screeps.com/img/c1.png)

新占领的房间控制器可以让你在该房间建造一个Spawn。如果需要建造额外的Spawn或者其他扩展就需要通过[`Creep.upgradeController`](https://docs.screeps.com/api/#Creep.upgradeController)给控制器输入能量来提升房间控制器等级（Room Controller Level，RCL）。

![](https://docs.screeps.com/img/c2.png)

## RCL等级对应可建造建筑

| RCL  | 升级所需能量 |                             建筑                             |
| :--: | :----------: | :----------------------------------------------------------: |
|  0   |      -       |                     Roads, 5 Containers                      |
|  1   |     200      |                 Roads, 5 Containers, 1 Spawn                 |
|  2   |    45,000    | Roads, 5 Containers, 1 Spawn, 5 Extensions (50 capacity), Ramparts (300K max hits), Walls |
|  3   |   135,000    | Roads, 5 Containers, 1 Spawn, 10 Extensions (50 capacity), Ramparts (1M max hits), Walls, 1 Tower |
|  4   |   405,000    | Roads, 5 Containers, 1 Spawn, 20 Extensions (50 capacity), Ramparts (3M max hits), Walls, 1 Tower, Storage |
|  5   |  1,215,000   | Roads, 5 Containers, 1 Spawn, 30 Extensions (50 capacity), Ramparts (10M max hits), Walls, 2 Towers, Storage, 2 Links |
|  6   |  3,645,000   | Roads, 5 Containers, 1 Spawn, 40 Extensions (50 capacity), Ramparts (30M max hits), Walls, 2 Towers, Storage, 3 Links, Extractor, 3 Labs, Terminal |
|  7   |  10,935,000  | Roads, 5 Containers, 2 Spawns, 50 Extensions (100 capacity), Ramparts (100M max hits), Walls, 3 Towers, Storage, 4 Links, Extractor, 6 Labs, Terminal |
|  8   |      -       | Roads, 5 Containers, 3 Spawns, 60 Extensions (200 capacity), Ramparts (300M max hits), Walls, 6 Towers, Storage, 6 Links, Extractor, 10 Labs, Terminal, Observer, Power Spawn |

## 攻击控制器

控制器无法被攻击或毁坏。然而，控制器在没有受到[`upgradeController`](https://docs.screeps.com/api/#Creep.upgradeController)的作用下会缓慢降级，比如说RCL1的时候20,000个游戏周期会降一级，具体的降级规则看[`StructureController`](https://docs.screeps.com/api/#StructureController)。当RCL等级到达0点时候，该房间控制器就变成中立的了，其他玩家就可以占领了。

当然你可以通过[`attackController`](https://docs.screeps.com/api/#Creep.attackController)影响别人的RC降级计时器。

![](https://docs.screeps.com/img/controllerDowngrade.png)

## 提升GCL

升级GCL需要向控制器中注入能量，GCL与控制器的级别是同步增长的，只要往控制器中注入能量GCL就会涨，即使控制器已经满级了。

一旦GCL级别提升了就不会再降下来，即使游戏输了一个房间都不剩了。重新开始游戏GCL仍然还是那么多，可以让你领先在起跑线上。

如果一个房间所需的RCL比你的高你可以通过[reserve](https://docs.screeps.com/api/#Creep.reserveController) 先预约。

![](<https://raw.githubusercontent.com/nofacer/pic_bed/master/my_blog/footer.jpg>)

