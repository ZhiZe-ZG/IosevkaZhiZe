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

## 关于编程字体的思考和计划

Unicode 试图把有史以来存留下来的人类图形符号收录在一起。但是，除了 Unicode Code Chart 之外，这些字符其实很难有一起出现的场景。因此，就字体设计的角度来说，其实大部分是在针对一个特定的 Unicode 子集进行设计。这些子集可以是某一种自然语言的文字，也可以是一些特定的交流场景。程序代码就可以算作其中之一，用于编程过程中字符显示的字体就是编程字体。

### 区分性

作为编程字体，首要的性质就是区分性。虽然绝大多数的程序代码使用的字符集就是区区 ASCII，但是其内容和普通的英语或者拉丁语文本有很大不同。

对于英语，拉丁语这样的自然语言而言，其字母的排列是有规律可循的。一般不存在全是辅音字母，没有元音字母的单词。但是由于程序代码并不要求朗读，因而任何字母组合在程序代码中都是可能的。在自然语言中对词汇识别不是特别重要的大小写到了程序代码中也变得至关重要。

在自然语言中，大写字母 `I` 和小写字母 `l` 长得像一点不是什么致命的问题。当 `Illness` 这样的单词出现时，你知道它肯定不会是三个 `I` 或三个 `l` 开头的单词。但是在程序代码中 `IIIness` 或者 `lllness` 完全可能是合乎语法的变量名。

所以，作为编程字体，每一对字符的字形之间的区别都要足够明显。有时为了凸显这种区分，给无衬线字体加上一些装饰衬线或者对字符写法做出变形调整也不是不可以。

### 等宽度

对于拉丁字母来说，每个字符不一定是等宽的，但是对于汉字来说，绝大多数印刷体汉字都是等宽的。这是两种不同的排印习惯，没有孰优孰劣。但是对于编程来说，人们更偏好等宽字体。

一方面来说这是历史原因导致的。因为早期设备的限制，等宽字体比非等宽字体更好制作，因此打字机和终端机往往采用等宽字体。

另一方面来说，等宽在编程中也更具功能性。因为等宽字体能相对直观准确地反映字符串的长度。在此基础上，还能进行矩形选中或者编辑。对于特定格式的代码文本来说，有很强的效率提升能力。另外等宽字体也是将字符视作像素，然后进行图表绘制的基础。

在考虑到 Unicode 覆盖的情况下，等宽度实际上具有一些挑战性。抛开 em-dash 和 en-dash 失去区分度这种相对细节的问题而言，主要有一个大问题——汉字和表情符号在一个拉丁字母的宽度下是很难显示的。

对此知则考虑了两种方案，一种是 1:2 方案。这为 Unifont 等字体所采用。所有汉字或表情符号设计为拉丁字母的两倍宽度。如果在此基础上每个拉丁字符的宽高比也设置为 1:2 那么两个拉丁字符或者一个汉字就正好构成一个方块。

另一种是全等宽方案。设每个字符字面高度为 1000，一般的拉丁字符宽度为 600, 汉字为 1000。如果拉丁字符拉宽至 700 或更宽，汉字压缩为 850 或更窄，就可能让汉字和拉丁字符完全等宽（小篆的长条形结构似乎暗示了这种方案的可行性，汉字不一定非得是正方形的结构）。

目前， [Source Han Mono](https://github.com/adobe-fonts/source-han-mono) 中的西文字体宽度扩展为 667， 而 [霞鹜铭心宋](https://github.com/lxgw/LxgwNeoZhiSong) 中的汉字字面宽度为 850 （得意黑似乎是 800）。因此合适的平衡点应当在此区间。

Iosevka ZhiZe 主要尝试 1:2 策略，后续有能力可以考虑尝试全等宽字体。

### Unicode 覆盖能力

传统来说，一份代码文件中不应当出现 ASCII 以外的其他字符。这是因为早先对于 ASCII 之外的部分，不同编码方案差异极大。即便是 Unicode 基本一统江湖的现在，不同环境中对于非 ASCII 的 Unicode 字符的处理也是有所差异的。因此，为了保证程序的准确性，不在代码中使用 ASCII 以外的字符是一个非常明智的做法。

不过在现在，只要能确保所有读写代码文件的环境都遵循 Unicode 规范。那么代码中出现非 ASCII 字符也是可以的。不过，考虑到不同编程语言对于非 ASCII 的 Unicode 字符支持程度不同。因此，一般来说，还是建议仅仅在注释或者字符串字面值中使用非 ASCII 字符。这样即便对非 ASCII 字符解析失败，一般也不会造成特别严重的后果。对于这种方案来说，编程字体支持非 ASCII 字符有了一定的意义，那就是在阅读注释或者检查字符串字面值的时候有一个比较连贯的体验。

以上的方案中，非 ASCII 字符还是处于一个相对低等的地位，只能作为数据或者注释存在。那么，是否有可能或者有必要将非 ASCII 引入实际的代码中呢？这是一个值得探讨的问题。首先应当考虑 ASCII 是否已经足够编程呢？

从理论上来说，哪怕只有两个彼此区别的字符，都足够编程了。因为它们可以进行无限的组合排列。但是对于人类来说，这样的系统显然不够友好。所以，拉丁字母和空格被引入了代码。这样人们就能使用熟悉的自然语言词汇命名标识符。

除了拉丁字母，其实其他任意一个自然语言的书写系统都可以担当此任。只不过拉丁字母在 ASCII 中占了先发优势。在这种情况下，其他书写系统只能作为补充系统进入。虽然补充其他书写系统中的字符可以增加基本字符的数量，但这也不见得是好事。

首先，补充进去的书写系统很可能和原有的字符有相似的，从而造成区分困难。例如拉丁字母中的 `A` 和希腊字母中的 `Α` （alpha）。

其次，基本字符数量太多会加重人的记忆负担。可能拼写单词是方便了，但是认字成了难题。习惯于西文拼写系统的人初次学汉字就会遇到类似的问题。

因此，仅仅从命名标识符的角度来说，有一套完备的自然语言符号就足够了。

但是显然， ASCII 中除了拉丁字母还有大量其他字符。例如阿拉伯数字。阿拉伯数字，本质上和拉丁字母类似，都是用于构成标识符的字符。但是它是相对拉丁字母的外来文字体系，因此分别用拉丁字母和阿拉伯数字组成的标识符一般表示两类不同的东西。例如常见的编程语言中，拉丁字母组成的标识符可以表示变量名，而纯粹由阿拉伯数字构成的标识符则表示数字的字面值。

这种分类用法当然是非常有意义的，但是如果每引入一个新的类群就加一种自然语言的书写系统，最后还是会导致字符集过于杂乱（例如数学和物理公式就是这样）。因此，现代的编程语言更倾向于用前后缀、标点符号或者类型标记之类的东西去标识一个标识符的类型（就像面向对象编程中表示类型那样）。

但是显然，这样的系统写出来会非常冗长例如一个简单的加法算式可能是这样的：

```text
one:number add:operator two:number
```

而我们实际想要:

```text
1 + 2
```

或者:

```text
1 `add` 2
```

第一种直接引入加法记号的方法，实际上还是在变相增加基本字符集数量。但是如果一个字符表示的含义足够重要和独特，那么这点代价也是值得的。因此，知则认为不考虑输入困难的情况下，引入 `×`， `÷`， `≥`， `≤` 和 `≠` 之类算符还是很有意义的。起码直接引入这些字符不会像用一些连写替换字体那样造成所见非所得的问题。

第二种情况也引入了新的符号，但是这个符号本身不表示一个具体的操作，而是用于表示被它标记的标识符属于某一个类群（在这里表示它是一个中缀算符）。这样仅仅引入一个算符就能解决一类标识符的问题。虽然相比直接为每一个运算引入一个符号来说它还是稍微冗长些，但是在可能用到的算符非常多时，为每一个运算引入一个符号显然是不可能的。

如果我们把新引入的符号本身用于作为类型标注的语法，那么用一个符号就足以给所有标识符标注类型，就像这样：

```text
1`num add`op 2`num
```

总的来说，知则对于编程语言实质使用非 ASCII 的看法是：首先每个语言应当有一个使用极少字符的内核。这个内核足以表示所有的代码逻辑。其次，可以系统性的针对一些常用的功能，引入专有的表示方法以精简代码增加可读性。

所以对于编程字体来说，也应该逐步专题性增加字符覆盖（例如把算术常用字符包括在内等）。不过这个专题是指符号之间的逻辑关联，而不一定是 Unicode 的 code block。

当然，考虑到英语等自然语言经常用于代码的注释书写。对这些自然语言的书写系统中的字符和标点进行系统支持也可以算作一种针对注释的支持（英语中 `café` 之类的还是当成外来语处理比较好，纯英语拼写去掉这些标注，因为英语本身没有定义这些标注的作用）。

最后，关于字体 Unicode 覆盖能力总结如下：

1. 首要保证 ASCII 覆盖
1. 以功能专题形式逐步拓展功能模块覆盖（每个模块要写说明说清增补内容和 ASCII 原有支持情况）
1. 为了方便多语言程序的调试，应该尽可能给实质程序代码之外的非 ASCII 以覆盖（实践中考虑以显示 Unicode 编号或直接引用 Unifont 的方式处理）

### 字符终端绘制

字符终端是一个颇具历史气息的编程工具。但是输入输出字符串确实是最基本的人机交互方式之一。

不少程序员喜欢将字符终端当作显示器使用，把字符当作像素来绘制各种表格或者图像。这类功能看起来比较花哨，确实算不上基本的编程需求。有人可能会说，直接用 GUI 界面不是更好么。

但是确实有一些情境中 GUI 显得比较笨重和复杂。而另一方面，纯粹的文字又显得不够醒目和清晰。因此 TUI 绘制也算是一个编程字体的需求点

目前的字符终端绘制主要通过基础字体的内置支持以及集成 Nerd Font 实现。但这里边其实有很多不协调。例如空格的高度和 Powerline 符号不太一样，还有 Powerline Extra 里的圆角符号并没有像尖角一样设置为宽度 530，而是设置为了 505。这导致一些情况下它和其他字符之间有缝隙。

后续考虑也以专题形式逐个模块地处理这些问题。

### 审美需求

* 简洁：每一个字符都不宜过度复杂，甚至越简单越好。不过该条类似区分性，仅对 ASCII 和扩展的功能模块起效。
* 统一：同一个书写系统或者系列的符号应当具有统一性，不同的系统之间要有区分度。另外字体整体要有一定的统一性。主要针对 ASCII 和扩展功能模块。

## To Do

* [ ] 参考 Nerd Font 的 patch 脚本写一个 patch 脚本，用于将 Nerd Font 和 Unifont 作为补丁打入。
* [ ] 增加 Iosevka 的 Bold, Oblique 和 Bold Oblique 生成。
* [ ] 合成字体时 ASCII 区域引用 Iosevka， 其他 Unicode 区域引用 Unifont， PUA 区域引用 Nerd Font。
* [ ] 为 Unifont 和 Nerd Font 生成 Bold, Oblique 和 Bold Oblique。
* [ ] 对 Unifont 和 Nerd Font 的部分字符做调整，尤其是 Nerd Font 的字宽问题。另外还有 Nerd Font 中 Powerline 部分字形由间隙这类小问题的修复。
* [ ] 更为完整的改动和更新列表。
