# 版本及问题和思路记录

## 版本

1. sNumCarSort.py ：最初版本，放车规则为一辆一辆放车
2. speedSort.py ：速度V1.0版本速度从大到小放车，每次17辆
3. speedTimeSort.py : 速度V2.0版本，在速度排序的基础上每次投放210辆，每次间隔9time再次放车，同时添加了对于channel和speed的惩罚和路线上车辆数量的反馈
4. speedTimeSort2.py：速度V2.1版本，在2.0的速度排序中再对出发时间进行了排序，但是没有测试车辆反馈的效果，同时惩罚无法使用speed，导致虽然是240+7但是效果不是很好，后期可以测试整理一下，排序那也许没有达到效果
5. speedTimeSort3.py：速度v2.2版本，添加了车辆反馈，对排序bug进行了一定的修复
6. speedTimeSort4.py：速度v2.3版本，排序中添加了起始点到出发点的坐标，并对直行进行了奖励（没奖励的并没有测试），使得每次投放是按照路径复杂度进行排序的投放，对地图的loss惩罚进行了优化修改
7. speedTimeSort4_1.py：速度v2.3.1版本,2.3的坐标排序并不是按照每次大小投放开始排序，而是先坐标排序，再投放，导致有时候并不是从近到远（一批远近有用？？？）
8. speedTimeSort4_2.py：速度v2.3.2版本,按照速度后对坐标排序，动态time

## 问题

1. 对于地图惩罚的优化没有利用到speed，目前只用到了channel
2. 分组优化更细节的进行思考
3. 按开始时间分组其实过了时间10以后已经无用
4. 动态time的优化，取消对前10发车的坐标排序

## 思路

1. 对于time和放车数的动态投放:time完成
2. 车数记录的优化
3. 考虑实时的路口拥堵和调整，对未来进行预估和规划
4. 车速和路速的匹配，拥堵的衡量标准（路长，车数）
5. 每张地图使用不同的参数

## 日历

3.26 完成V2.3版本base
3.27 分析了地图惩罚，loss进行了部分优化；思考思路1时发现坐标排序问题，分成两个思路，1.按每次投放固定从近到远。2.一个速度从近到远，动态time。完成2.3.2
