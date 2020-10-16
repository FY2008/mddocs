flex 是 flexible Box 的缩写，意为“弹性布局”，用来为盒状模型提供最大的灵活行性，任何容器都可以指定为 flex 布局。

* 当我们为父盒子设为 flex 布局后，子元素的 float、clear 和 vertical-align 属性将失效。
* 伸缩布局 = 弹性布局 = 伸缩盒布局 = 弹性盒布局 = flex 布局
* 采用 Flex 布局的元素，称为 Flex 容器（ flex container ），简称“容器”。它的所有子元素自动成为容器成员，称为 Flex 项目 （ flex item ），简称“项目”。
* 子容器可以横向排列也可以纵向排列

> **总结flex布局原理** 
>
> 就是通过给容器添加 flex 属性，来控制项目的位置和排列方式。

## 父容器 常见属性

一下有 6  个属性是对父容器设置的

* `flex-direction` ：设置主轴的方向
* `justify-content` : 设置主轴上的子元素排列方式
* `flex-wrap` : 设置子元素是否换行
* `align-content` : 设置侧轴上的子元素的排列方式（多行）
* `align-items` : 设置侧轴上的子元素排列方式（单行）
* `flex-flow` : 复合属性，相当于设置了 flex-direction 和 flex-wrap 

### flex-direction 设置主轴的方向

### 属性值

flex-direction 属性决定主轴的方向（即项目的排列方向）

==注意：主轴和侧轴是会变化的，就看 flex-direction 设置谁为主轴，剩下的就是侧轴。而我们的子元素是跟着主轴来排列的==

|     属性值     | 说明               |
| :------------: | ------------------ |
|      row       | 默认值从左到右排列 |
|  row-reverse   | 从右到左           |
|     column     | 从上倒下           |
| column-reverse | 从下到上           |

### justify-content 设置主轴上的子元素排列方式

justify-content 属性定义了项目在主轴上的对齐方式

==注意：使用这个属性之前一定要确定好主轴是哪个==

|    属性值     | 说明                                         |
| :-----------: | -------------------------------------------- |
|  flex-start   | 默认值 从头部开始，如果主轴是x轴，则从左到右 |
|   flex-end    | 从尾部开始排列                               |
|    center     | 延主轴居中对齐                               |
| space-around  | 平分剩余空间                                 |
| space-between | 先两边贴边，再平分剩余空间（重要）           |

### flex-wrap 设置是否换行

| 属性值 | 说明             |
| :----: | ---------------- |
| nowrap | 不换行（默认值） |
|  wrap  | 换行             |

### align-items 设置侧轴上的子元素排列方式（单行）

该属性是控制子项在侧轴上的排列方式，在子项为单项的时候使用

|   属性值   | 说明                                       |
| :--------: | ------------------------------------------ |
| flex-start | 默认值，从上到下                           |
|  flex-end  | 从下到上                                   |
|   center   | 挤在一起居中                               |
|  stretch   | 拉伸（子元素不能设置 height ，否则拉伸无效 |

### align-content 设置侧轴上的子元素的排列方式（多行）

设置子项在侧轴上的排列方式，并且只能用于子项出现换行的情况（多行），在单行下无效

|    属性值     | 说明                                   |
| :-----------: | -------------------------------------- |
|  flex-start   | 默认值在侧轴的头部开始排列             |
|   flex-end    | 在侧轴的尾部开始排列                   |
|    center     | 在侧轴中间显示                         |
| space-around  | 子项在侧轴评分剩余空间                 |
| space-between | 子项在侧轴先分布在两头，再平分剩余空间 |
|    stretch    | 设置子项元素高度平分父元素高度         |

### align-content 和 align-items 的区别

* align-items 适用于单行情况下，只有上对齐，下对齐，居中和拉伸
* align-content 适用于换行（多行）的情况下（单行情况下无效），可以设置上对齐，下对齐，剧中，拉伸以及平均分配剩余空间等属性值。
* 总结就是单行找 align-items，多行找 align-content

### flex-flow

flex-flow 属性是 flex-direction 和 flex-wrap 属性的复合属性

`flex-flow: row wrap;`

## 子元素常见属性

* flex 子项目占的份数
* align-self 控制子项目自己在侧轴的排列方式
* order 定义子项的排列顺序（前后顺序）

### flex 属性

flex 属性定义子项目分配剩余空间，用 flex 来表示占用多少份数。

```css
.item {
    flex: 1;
}
```

### align-self

align-self 属性允许单个项目与其它项目不一样的对齐方式，可覆盖 align-items属性。默认值为 auto,表示继承父元素的 align-items 属性。如果没有父元素则等同于 stretch。

```css
span:nth-child(2) {
    /* 设置自己在册轴上的排列方式 */
    align-self: flex-end;
}
```

### order 

order 属性定义项目的排列顺序，数值越小，排列越靠前，默认为0。

