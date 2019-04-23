> 原文链接：<https://docs.screeps.com/defense.html>
> 原创翻译，未经允许禁止转载。

# 保护房间

Screeps的世界危机重重，本文主要介绍保卫自己的领土不受入侵的方法。

## 安全模式

当你新开一局游戏的时候，房间的安全模式会被打开。这意味其他的creeps不能在你的房间里对你的creeps造成任何影响（但是你可以干爆他们，RUA！）。详细的介绍看[`StructureController`](https://docs.screeps.com/api/#StructureController)。

![](https://docs.screeps.com/img/safe_mode.png)

安全模式持续20,000个游戏周期（大约20小时，实际取决于每个游戏周期的具体时间）。如果room controller存有额外的激活次数也可以通过[`StructureController.activateSafeMode`](https://docs.screeps.com/api/#StructureController.activateSafeMode)手动激活：

```javascript
Game.rooms.W1N1.controller.activateSafeMode()
```

每一次升级时controller都会获得一次激活激活。除此之外还可以借助ghodium资源通过[`Creep.generateSafeMode`](https://docs.screeps.com/api/#Creep.generateSafeMode)增加激活次数。

安全模式是GG前的最后一道防线。但是一个镜像世界同时只能有一个房间被激活安全模式。因此不能依赖安全模式用来防御，而应该使用墙、城墙、塔、creep来加强房间的防御。

## 被动防御：墙（Walls）

最简单的防守方法就是在出生保护期内在合适的位置构建墙壁。和环境中天然的墙不同的是，建造的墙离房间边缘必须有2格以上的距离，并且可以被摧毁。因此只是建造墙还不够，还需要强化墙壁拖延对手的进攻时间。

![](https://docs.screeps.com/img/defense1.png)

墙的初始耐久只有**1点**。如果想要拖延敌人几小时（甚至几天）需要借助worker creep来进行强化[修复]([`repair`](https://docs.screeps.com/api/#Creep.repair))。墙的耐久最多可以修复到**300,000,000**点。如果资源氪够了，这样的一个墙可以抵御很多天的攻击。当然一个墙只有1个square，可以多氪一点弄几排墙出来就很6了。

## 被动防御：城墙（Ramparts）

墙有个弊端就是虽然可以阻止敌人，同时也会阻止自己的单位移动，阻碍己方势力的扩展。

这也是城墙的意义所在。城墙对敌人来说和墙一样，但是自己的单位却可以自由穿过。城墙还可以保护creep，在城墙被摧毁前，其中的单位是无敌的，而且还可以攻击敌人。

![](https://docs.screeps.com/img/defense2.png)

和普通的墙一样，城墙的初始耐久也是1点，最大的耐久值由控制器等级决定。在[之前的文章](https://zhuanlan.zhihu.com/p/61609387)中介绍过。

城墙和普通墙不一样的地方在于，每过几个游戏周期耐久值就会掉一点，所以需要分配工人保持城墙的耐久。

## 主动防御：塔（Towers）

被动的防御系统就算再强也有被破坏的一天，因此需要结合其他的一些机制来进一步提升防御效果。

![](https://docs.screeps.com/img/defense3.png)

在控制器等级3级以后就可以建造塔来进行主动防御。和墙与城墙不同，塔的防御是主动的，通过消耗能量塔可以攻击敌人、治疗己方单位以及修复建筑。

> 塔的作用范围为全房间，但是会随着距离衰减，所以尽量把塔放在合适的位置保证效果最大化。

塔的每一种操作会消耗10个能量单位，所以需要有单位保证塔的能源供应。

下面代码展示了如何利用塔攻击房间里的敌人：

```javascript
function defendRoom(roomName) {
    var hostiles = Game.rooms[roomName].find(FIND_HOSTILE_CREEPS);
    if(hostiles.length > 0) {
        var username = hostiles[0].owner.username;
        Game.notify(`User ${username} spotted in room ${roomName}`);
        var towers = Game.rooms[roomName].find(
            FIND_MY_STRUCTURES, {filter: {structureType: STRUCTURE_TOWER}});
        towers.forEach(tower => tower.attack(hostiles[0]));
    }
}
```

## 主动防御：Creeps

虽然塔可以用来主动防御，但是并不是万能的。当对面安排了一队分工合理的creeps来入侵时，是能够抵御多个塔楼的近距离攻击的。相对应的，我们也可以组织creeps来进行防守反击。

![](https://docs.screeps.com/img/defense4.png)

因为城墙可以保证在其面积上的单位免受任何形式的攻击，因此我们可以用这种形式组织防御阵型，不过要注意资源的分配，这么造还是挺耗资源的。

编写对应的AI代码不是很容易，但是确是保护房间不受任何入侵的唯一办法。

> 你可以在房间里生成[虚拟的入侵者]([NPC invader creeps](https://docs.screeps.com/invaders.html) )来测试你的防御系统。

总结一下，合理安排防守策略会使得房间很难被骚扰。但是俗话说的好，最好的防守是进攻，所以RUA！

![](<https://raw.githubusercontent.com/nofacer/pic_bed/master/my_blog/footer.jpg>)