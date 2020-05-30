## Form 窗口属性列表

### 布局

1. AutoScaleMode | 自动缩放模式，一般无需修改
2. AutoScroll | 是否自动缩放
3. AutoScrollMargin | 自动缩放外边距
4. AutoScrollMinSize | 自动缩放最小值
5. AutoSize | 自动大小
6. AutoSizeMode | 自动大小模式
7. Location | 窗口启动后的坐标位置
8. MaximumSize | 设置窗口最大值
9. MinimumSize | 设置窗口最小值
10. Padding | 内边距
11. Size | 默认大小
12. StartPosition
    1. WindowsDefaultLocation (默认值)
    2. CenterScreen (屏幕中心)
    3. WindowsDefaultBounds
    4. CenterParent (父窗口中心)
    5. Manual
13. WindowState (窗口默认大小状态)
    1. Normal (默认值)
    2. Minimized
    3. Maximized

### 窗口样式

1. ControlBox | 是否显示标题栏的控制按钮（右上角)
2. HelpButton (显示帮助按钮，要把最大化和最小化按钮禁用)
3. Icon (窗口标题栏图标)
4. isMdiContainer (是否是 Mdi 容器)
5. MainMenuStrip (主菜单)
6. MaximizeBox | 是否显示最大化按钮
7. MinimizeBox | 是否显示最小化按钮
8. Opacity (透明度 100%)
9. ShowIcon | 是否显示图标
10. ShowInTaskbar | 是否在任务栏显示
11. SizeGripStyle
    1. Auto (默认值)
    2. Show
    3. Hide
12. TopMost (显示到最顶层)
13. TransparencyKey (透明色)

## 行为

1. AllowDrop
2. AutoValidate
3. ContextMenuStrip
4. DoubleBuffered // 开启后可减少界面闪烁，如果有的话
5. Enabled // 是否可用
6. imeMode // 输入法模式设置

## 焦点

1. CausesValidation

## 可访问性 

辅助工具是专用的程序和设备，用于帮助残障人士更加有效地使用计算机。

1. AccessibleDescription
2. AccessibleName
3. AccessibleRole

## 设计

1. Name
2. Language | 选择语言
3. Localizable |  设置该属性为True后，.net 将根据不同的语言，为应用程序生成不同的资源文件
4. Locked | 在设计器里锁定窗口大小不可变

## 数据

### ApplicationSettings

1. PropertyBinding
2. Location
3. Text

### DataBindings

1. Advanced
2. Tag
3. Text

## 外观

1. BackColor // 背景颜色
2. BackgroundImage // 背景图片
3. BackgroundImageLayout // 背影图片布局方式
4. Cursor // 光标
5. Font
6. ForeColor // 前景色，字体颜色
7. FormBorderStyle // 边框样式
8. RightToLeft
9. RightToLeftLayout
10. Text
11. UseWaitCursor // 使用漏斗光标

##  杂项

1. AcceptButton // 确定按钮
2. CancelButton // 取消按钮
3. KeyPrreview // 

