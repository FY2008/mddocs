# Bulma-container的使用

`Bulma`是一个免费的开源`CSS`框架，基于`Flexbox`，已有200,000多名开发人员使用。

## Bulma  容器 | .container

`.container` 类可以用在任何地方，但主要用在如： `footer`,`navbar`,`section`,`hero`这样的顶层包裹标签。

## 默认容器 .container

```html
<div class="container">
  <div class="notification">
    This container is <strong>centered</strong> on desktop.
  </div>
</div>
```

每个 `breakpoint` 的 `containers` 宽度是: `$device - (2 * $gap)` 的结果。`$gap` 变量的默认值为32px，但是可以修改。

## 容器的最大宽度

* on `$desktop` it will have a maximum width of `960px`.
* on `$​widescreen` it will have a maximum width of `1152px`.
* on ​`$fullhd` it will have a maximum width of `1344px`.

选择 960,1152, 1344 是因为可以被 12 和 16 整除。

## container 断点修饰

1. `is-fluid`
2. `is-widescreen`
3. `is-fullhd`

容器文档：https://bulma.io/documentation/layout/container/

