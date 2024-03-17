# Iosevka ZhiZe

以下是 Iosevka ZhiZe 的描述 toml，编译方法详见 [Iosevka  的构建介绍](https://github.com/be5invis/Iosevka/blob/main/doc/custom-build.md) 和 [Iosevka 自定义工具页面](https://typeof.net/Iosevka/customizer)。

名称中的 `x00` 是用于表示版本号的两位十六进制数。这项参数在项目名称和编译命令以及输出文件的名称中起作用。

```toml
[buildPlans.IosevkaZhiZeX00]
family = "Iosevka ZhiZe x00"
spacing = "fixed"
serifs = "sans"
noCvSs = true
exportGlyphNames = true

[buildPlans.IosevkaZhiZeX00.variants.design]
capital-b = "standard-bilateral-serifed"
capital-d = "standard-bilateral-serifed"
capital-g = "toothless-corner-serifless-hooked"
capital-j = "serifless"
capital-p = "closed-motion-serifed"
capital-q = "crossing"
capital-r = "straight-top-left-serifed"
f = "tailed"
i = "serifed-semi-tailed"
k = "curly-serifless"
l = "serifed-semi-tailed"
v = "curly-serifless"
w = "curly-serifless"
x = "curly-serifless"
y = "curly-serifless"
z = "curly-serifless"
lower-chi = "straight-motion-serifed"
cyrl-capital-ze = "unilateral-serifed"
cyrl-ze = "unilateral-serifed"
cyrl-capital-ka = "straight-top-left-serifed"
cyrl-ka = "straight-top-left-serifed"
cyrl-em = "hanging-motion-serifed"
cyrl-en = "top-left-serifed"
cyrl-er = "eared-motion-serifed"
cyrl-capital-u = "straight-motion-serifed"
cyrl-u = "straight-motion-serifed"
zero = "oval-slashed"
one = "no-base-long-top-serif"
five = "oblique-arched"
eight = "two-circles"
asterisk = "hex-high"
ampersand = "et-tailed"
dollar = "interrupted-cap"
cent = "bar-interrupted-cap"

[buildPlans.IosevkaZhiZeX00.weights.Regular]
shape = 400
menu = 400
css = 400

[buildPlans.IosevkaZhiZeX00.weights.Bold]
shape = 700
menu = 700
css = 700

[buildPlans.IosevkaZhiZeX00.widths.Normal]
shape = 500
menu = 5
css = "normal"

[buildPlans.IosevkaZhiZeX00.slopes.Upright]
angle = 0
shape = "upright"
menu = "upright"
css = "normal"

[buildPlans.IosevkaZhiZeX00.slopes.Oblique]
angle = 9.4
shape = "oblique"
menu = "oblique"
css = "oblique"
```

编译命令

```shell
npm run build -- ttf::IosevkaZhiZeX00
```

以下是主要的设置和调整：

* 整体设置
  * 基于 Fixed ，关闭连写，严格的终端模式。
  * 移除 Italic ，统一样式，减少字体文件规模。
  * 宽度 500， 移除其他宽度
  * 移除部分字重
* 大写字母调整： 衬线调整，简化取消一些衬线同时同步增加一些衬线
  * B D P R 增加左侧衬线出头，方便 D 和 O 以及 B 和 8 的区分。而 P 和 R 是为了和 B 以及 D 保持一致。
  * G J 取消部分衬线
  * Q 更简洁的右下角斜线模式
* 小写字母调整： 曲线化，出头更多
  * f 拉长到和 j 相当，增加尾巴保持和 i l j 风格一致
  * i 增强曲线感，和 l 的修改保持一定统一，和原有的 j 的 serif 保持一致
  * l 使用不会被误认为 1 的写法，同时增强曲线感
  * k v w x y z 使用曲线感更强的字体
* 数字调整: 尺寸和大写字母一致，但是曲线和斜线更多
  * 0 使用椭圆形，和 O 在外形轮廓上做进一步区分
  * 1 使用长斜线写法
  * 5 使用斜竖线和平中线
  * 8 使用两个圈拼接的
* 字母衍生符号调整
  * $ 采用更矮的字形，竖线断开（与默认的 % 表现类似）
  * & 采用 Et 写法
* 成对符号调整（未进行调整， Iosevka 的正反斜杠看起来也是对称的）
* 其他 ASCII 符号调整
  * \* 采用六角竖线垂直写法（和 Unicode 文件上一致）
* 其他书写系统调整
  * 希腊字母 χ 增加衬线和 拉丁字母 X x 区别
  * 西里尔字母 З з 增加衬线和 ASCII 数字 3 区别
  * 西里尔字母 К к 增加衬线和拉丁字母 K k 区别
  * 西里尔字母 У у 增加衬线和拉丁字母 Y y 区别
  * 西里尔字母 м 增加衬线和拉丁字母 M m 区别
  * 西里尔字母 н 增加衬线和拉丁字母 H h 区别
  * 西里尔字母 р 增加衬线和拉丁字母 P p 区别
* 非 ASCII 拉丁调整
  * ¢ 采用和 S 相同的尺寸和风格

以下是 VS Code 中推荐的字体使用方案：

```text
'Iosevka ZhiZe x00', 'Unifont', 'Unifont Upper', 'Unifont CSUR'
```

## Nerd Font

该字体可以通过 Nerd Font 的 patcher 程序增补 Nerd Font 字符。

详情参见 <https://github.com/ryanoasis/nerd-fonts>。

fontforge 可以直接通过 winget 安装，安装后似乎不需要另行配置 Python 和 Python 包（不过我的机器上有 Conda 的 base 环境，不知道这个有没有影响）。

需要注意的是如果要增补全部的 Nerd Font，需要添加参数 `-c`，例如：

```shell
fontforge -script font-patcher -c PATH_TO_FONT
```
