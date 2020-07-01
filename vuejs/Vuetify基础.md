# Vuetify 基础

## 样式和动画

### CSS Reset (CSS 重置)

Vuetify 有一套自己的 CSS 基础代码重置库 ress。[详情链接](https://vuetifyjs.com/zh-Hans/styles/css-reset/)

### Border Radius （圆角边框）

1. `.rounded-sm` `.rounded` `.rounded-lg` `.rounded-xl`
2. `.rounded-pill` `.rounded-circle`
3. `.rounded-0`
4. `.rounded-t-xl` `.rounded-r-xl` `.rounded-b-xl` `.rounded-l-xl`
5. `.rounded-tl-xl` `.rounded-tr-xl` `.rounded-br-xl` `.rounded-bl-xl`

## 文本样式

### Text alignment (文本对齐)

```html
<template>
  <p class="text-justify">
    Morbi mattis ullamcorper velit. Donec orci lectus, aliquam ut, faucibus non, euismod id, nulla. Fusce convallis metus id felis luctus adipiscing. Aenean massa. Vestibulum purus quam, scelerisque ut, mollis sed, nonummy id, metus.
  </p>
</template>
<template>
  <div>
    <p class="text-left">Left aligned text on all viewport sizes.</p>
    <p class="text-center">Center aligned text on all viewport sizes.</p>
    <p class="text-right">Right aligned text on all viewport sizes.</p>

    <p class="text-sm-left">Left aligned text on viewports sized SM (small) or wider.</p>
    <p class="text-md-left">Left aligned text on viewports sized MD (medium) or wider.</p>
    <p class="text-lg-left">Left aligned text on viewports sized LG (large) or wider.</p>
    <p class="text-xl-left">Left aligned text on viewports sized XL (extra-large) or wider.</p>
  </div>
</template>
```

### Text decoration（文本修饰）

```html
<template>
  <div>
    <a href="#" class="text-decoration-none">Non-underlined link</a>

    <div class="text-decoration-line-through">Line-through text</div>

    <div class="text-decoration-overline">Overline text</div>

    <div class="text-decoration-underline">Underline text</div>
  </div>
</template>
```

### 文本截断

`.text-truncate`

### 文本大小写转换

```html
<template>
  <div>
    <p class="text-lowercase">Lowercased text.</p>
    <p class="text-uppercase">Uppercased text.</p>
    <p class="text-capitalize">CapiTaliZed text.</p>
  </div>
</template>
```

### 文本字体样式

```html
<template>
  <div>
    <p class="font-weight-black">Black text.</p>
    <p class="font-weight-bold">Bold text.</p>
    <p class="font-weight-medium">Medium weight text.</p>
    <p class="font-weight-regular">Normal weight text.</p>
    <p class="font-weight-light">Light weight text.</p>
    <p class="font-weight-thin">Thin weight text.</p>
    <p class="font-italic">Italic text.</p>
  </div>
</template>
```

### 文本透明度 (Text opacity)

```html
<template>
  <div>
    <p class="text--primary">High-emphasis has an opacity of 87%.</p>
    <p class="text--secondary">Medium-emphasis text and hint text have opacities of 60%.</p>
    <p class="text--disabled">Disabled text has an opacity of 37%.</p>
  </div>
</template>
```

### RTL Alignment

```html
<template>
  <div>
    <p class="subtitle-2 text-center">Agnostic RTL Alignment</p>

    <p class="text-sm-left">Left aligned text on viewports sized SM (small) or wider for rtl or ltr.</p>
    <p class="text-md-left">Left aligned text on viewports sized MD (medium) or wider for rtl or ltr.</p>
    <p class="text-lg-right">Right aligned text on viewports sized LG (large) or wider for rtl or ltr.</p>
    <p class="text-xl-left">Left aligned text on viewports sized XL (extra-large) or wider for rtl or ltr.</p>

    <p class="subtitle-2 text-center">Responsive RTL Alignment</p>

    <p class="text-start">Left aligned text on ltr and right aligned on rtl.</p>
    <p class="text-end">Right aligned text on ltr and left aligned on rtl.</p>
  </div>
</template>
```

### 文本颜色(red -> 背景色 red--text 文本色)

[https://vuetifyjs.com/en/styles/colors/](https://vuetifyjs.com/en/styles/colors/)

## 内容 (content)

### 引用块

```html
<template>
  <blockquote class="blockquote">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Harum maiores modi quidem veniam, expedita quis laboriosam, ullam facere adipisci, iusto, voluptate sapiente corrupti asperiores rem nemo numquam fuga ab at.</blockquote>
</template>
```

### 段落 (Paragraphs)

```html
<template>
  <div>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Harum maiores modi quidem veniam, expedita quis laboriosam, ullam facere adipisci, iusto, voluptate sapiente corrupti asperiores rem nemo numquam fuga ab at.</p>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Harum maiores modi quidem veniam, expedita quis laboriosam, ullam facere adipisci, iusto, voluptate sapiente corrupti asperiores rem nemo numquam fuga ab at.</p>
  </div>
</template>
```

### 代码 (Code)

```html
<template>
  <div>
    Example of an inline <code>&lt;code&gt;</code> element.
  </div>
</template>
```

### 变量 （Variables）

```html
<template>
  <div>
    <var>v</var> = <var>u</var> * <var>e</var>
  </div>
</template>
```

### User input

```html
<template>
  <div>
    To install Vuetify, type <kbd>npm install vuetify</kbd> into your console. Once complete, type <kbd>cd <code>&lt;project name&gt;</code></kbd> and run <kbd>npm install</kbd>
  </div>
</template>
```

## Display

### 断点

| Device      | Code | Types                  | Range               |
| ----------- | :--: | ---------------------- | ------------------- |
| Extra       |  xs  | small to large handset | < 600px             |
| Small       |  sm  | small to medium tablet | 600px > < 960px     |
| Medium      |  md  | large tablet to laptop | 960px > < 1264px*   |
| Large       |  lg  | desktop                | 1264px* > < 1904px* |
| Extra large |  xl  | 4k and ultra-wides     | > 1904px*           |

### Display

指定元素的 display 属性，方式： `.d-{value}` 或 `.d-{breakpoint}-{value}` `sm`,`md`,`lg`,`xl`

#### {value} 的值

* none
* inline
* inline-block
* block
* table
* table-cell
* table-row
* flex
* inline-flex

链接: https://vuetifyjs.com/en/styles/display/

## Float

* `.float-left`
* `.float-right`
* `.float-none`
* `.float-sm-left`
* `.float-sm-right`
* `.float-sm-none`
* `.float-md-left`
* `.float-md-right`
* `.float-md-none`
* `.float-lg-left`
* `.float-lg-right`
* `.float-lg-none`
* `.float-xl-left`
* `.float-xl-right`
* `.float-xl-none`

## 间距 (Spacing)

## margin 和 padding

* `m` - applies `margin`
* `p` - applies `padding`

### 指定方向

* t
* b
* l
* r
* s
* e
* x
* y
* a

### 大小

* 0
* 1
* 2
* 3
* 4
* 5
* 6
* 7
* 8
* 9
* 10
* 11
* 12
* 13
* 14
* 15
* 16
* n1 // n开头的只能用在 margin 上，n1 = -4px
* n2 = -8px
* n3 = -12px
* n4
* n5
* n6
* n7
* n8
* n9
* n10
* n11
* n12
* n13
* n14
* n15
* n16
* auto

## 文字与排版 （Text and typography）

1. Font
2. Weight
3. Size
4. Letter spacing

## Transitions (专场)

https://vuetifyjs.com/en/styles/transitions/

# Vuetify 组件



