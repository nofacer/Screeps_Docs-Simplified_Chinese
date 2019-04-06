> 原文链接：<https://docs.screeps.com/creeps.html>
> 原创翻译，未经允许禁止转载。

# Creeps

和其他RTS游戏一样，你的可控制单位被称为Creeps。但是Screeps炫酷的地方在于每一个Creep可以用7种可用的身体部位类型构造，每个单位上最多可以有50个部件。可以利用此机制构造出不同类型的Creeps：普通工人，能够在几个周期内建造或修复结构的巨型建筑机器，大容量运输单位，快速廉价的侦察兵，装备精良的具有再生能力的战斗机等。没有做不到，只有想不到。

​​​![](https://docs.screeps.com/img/bodyparts.png)

不过要注意的是Creeps只有1500个游戏生命周期（大约30-60分钟，具体取决于每个游戏周期时间）， 然后它会死掉。 因此，你不仅需要控制现有的小兵，还需要设计Creeps的更替方式。

标准的Spawn只能产生花费不超过300的基本的Creep。想要生产高级的Creep就需要建造Spawn扩展，每个Spawn扩展可使得Spawn的能量存储容量多50，从而可以生产更高级的Creeps。

Spawn扩展的放置位置不重要，只需要和Spawn在一个房间里就行了，并且一个扩展可以被多个Spawn共同使用。生产Creeps前需要Spawn和扩展里有足够多的能量。

一个房间里可以放置的扩展数量取决于房间的控制水平。详细的说明在[Global control](https://docs.screeps.com/control.html)里。

## Creeps技能

每个Creep的技能由Creep的构造部件决定：

* `WORK`-收集能量，建造和修复结构，升级控制器。
* `MOVE`-移动。
* `CARRY`-运输能源。
* `ATTACK`-短距离攻击。
* `RANGED_ATTACK`-长距离攻击。
* `HEAL`-治疗其他单位。
* `CLAIM`-控制领土。
* `TOUGH`-增加耐久。

每种能力的强弱取决于对应部件的数量。比如说有3个WORK部件的Creep的工作效率是只有一个WORK部件的Creep的工作效率的3倍。

## Movement

除了`MOVE`外，Creep的每一个构造部件都有重量，如果带的部件越多移动速度也越慢。每个部件（除了`MOVE`）都都会产生疲劳值：在道路上为1点，平原上为2点，沼泽里为10点。每一个MOVE部件每个游戏周期会减少2点疲劳值，当Creep的疲劳值大于0时无法移动。

> 如果要保证Creep每个游戏周期能移动一格，需要计算除`MOVE`外的所有部件的 疲劳值的和并使`MOVE`减少的疲劳值不低于这个总和。

值得注意的是没有搬运能源的 `CARRY`部件是不会产生疲劳的。

几个小例子：

* Creep `[CARRY,WORK,MOVE]`在没有搬运能量的时候一个周期可以跑一格，搬了能量以后2个周期才能跑1格。

* Creep `[TOUGH,ATTACK,ATTACK,MOVE,MOVE,MOVE]`将以满速（1个周期一格）行动。
* Creep `[TOUGH,ATTACK,ATTACK,MOVE,MOVE]`根据四舍五入原则2个周期移动一格。

## 伤害

每个creep可以承受的伤害总量由部件总数决定，每个部件可以增加100点耐久。被攻击时，排在前面的部件会被优先攻击，当部件完全损毁时，Creep就不再有对应能力了。

