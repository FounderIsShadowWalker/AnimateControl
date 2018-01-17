# AnimateControl
一个动画管理方案

想写一个动画管理动画队列，比较类似于ppt那种动画时间线

例如 A动画 {
    发生物体: 方块1
    动画：右移200px
    时间：500ms
    延迟: 100ms
    起始: null    //null 默认最开始的动画，即开场动画
}

   B动画{
       发生物体: 方块2
       动画: 旋转40deg
       时间: 1s
       延迟: 200ms
       起始：A   //B动画将在A动画后
   }  

动画管理工具会依据起始的时间线生成对应的动画方案

100ms -> A

1s + 500ms -> B

假定这个队列为Q, Queue 将提供一下API

update: 每一个动画做完都会掉用 算事动画的callback

skip: 跳过动画 例如 skip(A)，跳过动画A skip([A,B]) 跳过动画A,B

pause: 停止当前动画

play: 动画接着执行

redo: 重做动画   redo(A)， A会被做两遍
