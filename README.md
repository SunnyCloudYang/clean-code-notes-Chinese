# 《代码整洁之道》笔记

翻译自[JuanCrg90/Clean-Code-Notes](https://github.com/JuanCrg90/Clean-Code-Notes)，原书作者为Robert C. Martin。

- [第一章 整洁代码](#第一章-整洁代码)
  - [为什么要写糟糕的代码？](#为什么要写糟糕的代码)
  - [什么是整洁的代码？](#什么是整洁的代码)
  - [童子军规则](#童子军规则)
- [第二章 有意义的命名](#第二章-有意义的命名)
  - [使用有意义的命名](#使用有意义的命名)
  - [避免误导性命名](#避免误导性命名)
  - [做有意义的区分](#做有意义的区分)
  - [使用可发音的命名](#使用可发音的命名)
  - [使用可搜索的命名](#使用可搜索的命名)
  - [避免编码](#避免编码)
  - [避免思维映射](#避免思维映射)
  - [类名](#类名)
  - [方法名](#方法名)
  - [不要使用俏皮命名](#不要使用俏皮命名)
  - [每个概念对应一个词](#每个概念对应一个词)
  - [不要双关](#不要双关)
  - [使用解决方案领域的名称](#使用解决方案领域的名称)
  - [使用问题领域的名称](#使用问题领域的名称)
  - [添加有意义的上下文](#添加有意义的上下文)
  - [不要添加无意义的上下文](#不要添加无意义的上下文)
- [第三章 函数](#第三章-函数)
  - [小！！](#小)
  - [只做一件事](#只做一件事)
  - [每个函数一个抽象层级](#每个函数一个抽象层级)
  - [Switch 语句](#switch-语句)
  - [使用描述性名称](#使用描述性名称)
  - [函数参数](#函数参数)
  - [输出参数](#输出参数)
  - [命令与查询分离](#命令与查询分离)
  - [优先使用异常而不是返回错误码](#优先使用异常而不是返回错误码)
  - [不要重复自己](#不要重复自己)
  - [结构化编程](#结构化编程)
- [第4章 注释](#第4章-注释)
  - [注释不能弥补糟糕的代码](#注释不能弥补糟糕的代码)
  - [用代码解释自己](#用代码解释自己)
  - [好的注释](#好的注释)
  - [糟糕的注释](#糟糕的注释)
- [第5章 格式化](#第5章-格式化)
  - [垂直格式化](#垂直格式化)
  - [水平格式化](#水平格式化)
  - [缩进](#缩进)
  - [团队规则](#团队规则)
- [第6章 对象和数据结构](#第6章-对象和数据结构)
  - [数据抽象](#数据抽象)
  - [数据/对象的反对称性](#数据对象的反对称性)
  - [德米特法则](#德米特法则)
  - [数据传输对象](#数据传输对象)
- [第7章 错误处理](#第7章-错误处理)
  - [使用异常而不是返回错误码](#使用异常而不是返回错误码)
  - [首先编写 Try-Catch-Finally 语句](#首先编写-try-catch-finally-语句)
  - [提供异常的上下文](#提供异常的上下文)
  - [不要返回 null](#不要返回-null)
  - [不要传递 null](#不要传递-null)
- [第8章 边界](#第8章-边界)
  - [使用第三方代码](#使用第三方代码)
  - [探索和学习边界](#探索和学习边界)
  - [学习测试比免费更好](#学习测试比免费更好)
  - [使用尚未存在的代码](#使用尚未存在的代码)
  - [保持清晰的边界](#保持清晰的边界)
- [第九章 单元测试](#第九章-单元测试)
  - [TDD 的三条法则](#tdd-的三条法则)
  - [干净的测试](#干净的测试)
  - [每个测试一个断言](#每个测试一个断言)
  - [每个测试一个概念](#每个测试一个概念)
  - [F.I.R.S.T](#first)
- [第十章 类](#第十章-类)
- [类的组织](#类的组织)
  - [封装](#封装)
- [类应该小巧](#类应该小巧)
  - [单一职责原则](#单一职责原则)
  - [内聚性](#内聚性)
  - [保持内聚性会导致许多小类](#保持内聚性会导致许多小类)
- [为变化而组织](#为变化而组织)
  - [隔离变化](#隔离变化)
- [第11章 系统](#第11章-系统)
- [将系统构建与使用分离](#将系统构建与使用分离)
  - [与 main 分离](#与-main-分离)
  - [依赖注入](#依赖注入)
- [第12章 涌现](#第12章-涌现)
- [第13章 并发](#第13章-并发)
- [神话和误解](#神话和误解)
- [第14章 逐步改进](#第14章-逐步改进)
- [第15章 JUnit 内部](#第15章-junit-内部)
- [第16章 重构 SerialDate](#第16章-重构-serialdate)
- [第17章 代码风格和启发式方法](#第17章-代码风格和启发式方法)
- [总结](#总结)
  - [注释](#注释)
  - [环境](#环境)
  - [函数](#函数)
  - [通用](#通用)
  - [命名](#命名)
  - [测试](#测试)

## 第一章 整洁代码

这本书探讨的是优秀的编程实践。它讲述了如何编写优质的代码，以及如何将糟糕的代码转化为优质的代码。

代码体现了需求的细节，而这些细节既不能被忽视，也不能被抽象掉。我们或许可以创造出更接近需求的语言，也可以开发工具来帮助我们解析这些需求并将其组织成规范的结构。然而，我们永远无法消除对精确性的必要追求。

### 为什么要写糟糕的代码？

- 你是否在赶时间？
- 你是否试图“快速”完成任务？
- 你是否没有时间把工作做好？
- 你是否厌倦了在同一个程序/模块中工作？
- 你的老板是否在催促你尽快完成？

上述理由可能会让你陷入一片毫无意义的代码沼泽中。

如果你说“我稍后再回来修复它”，你可能会陷入 [LeBlanc 定律](https://en.wikipedia.org/wiki/Talk%3AList_of_eponymous_laws#Proposal_to_add_LeBlanc.27s_law) 的陷阱：“稍后等于永不”。

你是一名专业人士，代码是你的责任。让我们分析以下这个例子：

> 如果你是一名医生，而你的病人要求你停止手术前所有繁琐的洗手准备，因为这浪费了太多时间，你会怎么做？显然，病人是“老板”；然而，医生绝对应该拒绝这种要求。为什么？因为医生比病人更清楚疾病和感染的风险。如果医生听从病人的要求，那将是非常不专业的（更不用说违法了）。

同样，程序员屈从于那些不理解代码混乱风险的管理者的意愿，也是不专业的。

也许有时你会为了赶工期而想着快速完成任务。但唯一能真正快速前进的方法，就是始终保持代码尽可能的整洁。

### 什么是整洁的代码？

每个有经验的程序员对整洁代码都有自己的定义，但有一点是明确的：整洁的代码是易于阅读的代码。整洁的代码是经过精心维护的代码。

在书中，Bob 大叔（Uncle Bob）这样说道：

> 请将本书视为对“Object Mentor 整洁代码学派”的描述。书中的技术和教导是我们实践这门艺术的方式。我们相信，如果你遵循这些教导，你将享受到我们所享受的益处，并学会编写整洁且专业的代码。但不要误以为我们在某种绝对意义上是“正确”的。还有其他学派和其他大师，他们同样拥有专业性的主张。你也应该向他们学习。

### 童子军规则

仅仅写好代码是不够的。代码必须随着时间的推移保持整洁。我们都见过代码随着时间推移而腐化和退化。因此，我们必须积极采取措施来防止这种退化。

遵循 [童子军规则](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule) 是一个很好的实践：

> 始终让营地比你发现时更干净。

## 第二章 有意义的命名

命名在软件中无处不在。文件、目录、变量、函数等等都需要命名。因为我们在命名上花费了大量时间，所以我们应该把它做好。

### 使用有意义的命名

命名应该能够清晰地表达意图。选择好的命名需要时间，但它节省的时间会更多。因此，请认真对待命名，并在找到更好的命名时及时修改。

变量、函数或类的名称应该回答所有重要的问题。它应该告诉你它为什么存在、它做什么以及如何使用它。**如果一个名称需要注释来解释，那么这个名称就没有清晰地表达其意图**。

| 未表达意图的命名                | 表达意图的命名            |
| -------------------------------- | ----------------------- |
| `int d; // 经过的天数`           | `int elapsedTimeInDays` |

选择能够表达意图的命名可以使代码更容易理解和修改。例如：

```java
public List<int[]> getThem() {
  List<int[]> list1 = new ArrayList<int[]>();
  for (int[] x : theList)
    if (x[0] == 4)
      list1.add(x);
  return list1;
}
```

这段代码很简单，但会引发许多问题：

1. `theList` 的内容是什么？
2. `x[0]` 在列表中代表什么？
3. 为什么要将 `x[0]` 与 `4` 进行比较？
4. 返回的列表如何使用？

这些问题的答案在代码中并未体现，但它们本可以体现。假设我们正在开发一个扫雷游戏。我们可以将上述代码重构如下：

```java
public List<int[]> getFlaggedCells() {
  List<int[]> flaggedCells = new ArrayList<int[]>();
  for (int[] cell : gameBoard)
    if (cell[STATUS_VALUE] == FLAGGED)
      flaggedCells.add(cell);
  return flaggedCells;
}
```

现在我们可以清楚地知道以下信息：

1. `theList` 代表 `gameBoard`（游戏棋盘）
2. `x[0]` 代表棋盘上的一个单元格，`4` 代表被标记的单元格
3. 返回的列表代表 `flaggedCells`（被标记的单元格）

注意，代码的简洁性并没有改变。它仍然有相同数量的运算符和常量，嵌套层级也完全相同。但代码变得更加清晰明了。

我们可以通过为单元格编写一个简单的类来进一步改进代码，而不是使用 `int` 数组。这个类可以包含一个**表达意图的函数**（例如 `isFlagged`），以隐藏魔法数字。最终，函数的功能得到了进一步优化。

```java
public List<Cell> getFlaggedCells() {
  List<Cell> flaggedCells = new ArrayList<Cell>();
  for (Cell cell : gameBoard)
    if (cell.isFlagged())
      flaggedCells.add(cell);
  return flaggedCells;
}
```

### 避免误导性命名

程序员必须避免留下模糊代码含义的错误线索。我们应该避免使用那些与我们本意不符的词汇。

不要将一组账户称为 `accountList`，除非它确实是一个 `List`。`List` 这个词对程序员有特定的含义。如果存放账户的容器实际上不是 `List`，这可能会导致误解。因此，使用 `accountGroup`、`bunchOfAccounts` 或者简单的 `accounts` 会更合适。

小心使用那些只有细微差别的名称。在一个模块中看到 `XYZControllerForEfficientHandlingOfStrings`，而在稍远的地方看到 `XYZControllerForEfficientStorageOfStrings`，你能多快发现它们之间的细微差别？这些词的形状非常相似，容易混淆。

### 做有意义的区分

程序员在编写代码时，如果只是为了满足编译器或解释器的要求，往往会给自己制造麻烦。例如，因为在同一作用域中不能使用相同的名称来引用两个不同的东西，你可能会随意更改一个名称。有时这会通过拼写错误来实现，导致一种令人惊讶的情况：修正拼写错误后，代码反而无法编译。例如，你创建了一个变量 `klass`，因为 `class` 这个名称已经被其他东西占用了。

在下面的函数中，参数名称没有提供任何信息，`a1` 和 `a2` 无法体现作者的意图：

```java
public static void copyChars(char a1[], char a2[]) {
  for (int i = 0; i < a1.length; i++) {
    a2[i] = a1[i];
  }
}
```

我们可以通过选择更具描述性的参数名称来改进代码：

```java
public static void copyChars(char source[], char destination[]) {
  for (int i = 0; i < source.length; i++) {
    destination[i] = source[i];
  }
}
```

无意义的区分词（噪声词）是另一种无意义的区分方式。假设你有一个 `Product` 类，如果你还有另一个类叫 `ProductInfo` 或 `ProductData`，你只是让名称变得不同，但并没有让它们的含义有所不同。`Info` 和 `Data` 是像 `a`、`an` 和 `the` 这样的无意义噪声词。

噪声词是冗余的。变量名中不应该出现 `variable` 这个词，表名中也不应该出现 `table` 这个词。

### 使用可发音的命名

想象一下，你有一个变量 `genymdhms`（表示生成日期、年、月、日、小时、分钟和秒），然后想象在一次对话中你需要谈论这个变量，称它为“gen why emm dee aich emm ess”。你可以考虑将这样的类进行转换：

```java
class DtaRcrd102 {
  private Date genymdhms;
  private Date modymdhms;
  private final String pszqint = "102";
  /* ... */
};
```

转换为：

```java
class Customer {
  private Date generationTimestamp;
  private Date modificationTimestamp;;
  private final String recordId = "102";
  /* ... */
};
```

### 使用可搜索的命名

单字母名称和数字常量在文本中不容易被找到，这会带来特定的问题。

### 避免编码

我们已经需要处理足够多的编码了，不要再增加额外的负担。将类型或作用域信息编码到名称中只会增加解密的负担。编码后的名称通常难以发音，也容易拼错。例如，使用 [匈牙利命名法](https://en.wikipedia.org/wiki/Hungarian_notation) 或成员前缀就是这种情况。

#### 接口和实现

有时这是编码的一个特例。例如，假设你正在构建一个用于创建形状的抽象工厂（ABSTRACT FACTORY）。这个工厂将是一个接口，并由一个具体类实现。你应该如何命名它们？`IShapeFactory` 和 `ShapeFactory` 吗？最好不对接口进行修饰。我不希望用户知道我在传递一个接口，我只希望他们知道这是一个 `ShapeFactory`。因此，如果我必须对接口或实现进行编码，我会选择对实现进行编码。将其命名为 `ShapeFactoryImp`，甚至是丑陋的 `CShapeFactory`，都比对接口进行编码要好。

### 避免思维映射

读者不应该在脑海中将你的名称翻译成他们已经知道的其他名称。

聪明的程序员和专业的程序员之间的一个区别是，专业程序员明白清晰性至关重要。专业人士会利用他们的能力编写出易于他人理解的代码。

### 类名

类和对象的名称应该是名词或名词短语，例如 `Customer`、`WikiPage`、`Account` 和 `AddressParser`。避免在类名中使用诸如 `Manager`、`Processor`、`Data` 或 `Info` 这样的词。类名不应该是动词。

### 方法名

方法的名称应该是动词或动词短语，例如 `postPayment`、`deletePage` 或 `save`。访问器、修改器和断言方法应根据其值命名，并按照 JavaBean 标准前缀为 `get`、`set` 和 `is`。

当构造函数重载时，使用描述参数的静态工厂方法。例如：

```java
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

通常比以下方式更好：

```java
Complex fulcrumPoint = new Complex(23.0);
```

考虑通过将相应的构造函数设为私有来强制使用这些方法。

### 不要使用俏皮命名

| 俏皮命名           | 清晰命名      |
| ----------------- | ------------- |
| `holyHandGranade` | `deleteItems` |
| `whack`           | `kill`        |
| `eatMyShorts`     | `abort`       |

### 每个概念对应一个词

为一个抽象概念选择一个词并坚持使用它。例如，在不同的类中使用 `fetch`、`retrieve` 和 `get` 作为等效方法会让人感到困惑。

### 不要双关

避免将同一个词用于两个不同的目的。对两个不同的概念使用相同的术语本质上是一种双关。

例如：在一个类中使用 `add` 来表示通过加法或连接两个现有值来创建新值，而在另一个类中使用 `add` 来表示将简单参数放入集合中。更好的选择是使用 `insert` 或 `append` 这样的名称。

### 使用解决方案领域的名称

记住，阅读你代码的人将是程序员。因此，可以放心使用计算机科学（CS）术语、算法名称、模式名称、数学术语等。

### 使用问题领域的名称

当没有“程序员术语”来描述你所做的事情时，使用问题领域的名称。至少维护你代码的程序员可以向领域专家询问其含义。

### 添加有意义的上下文

有些名称本身是有意义的，但大多数并非如此。相反，你需要通过将名称放在良好命名的类、函数或命名空间中来为读者提供上下文。当所有其他方法都失败时，作为最后的手段，可能需要为名称添加前缀。

例如变量：`firstName`、`lastName`、`street`、`city`、`state`。放在一起时，它们显然构成了一个地址，但如果你在一个方法中看到单独使用的 `state` 变量呢？你可以通过添加前缀来提供上下文，例如 `addrState`，这样读者就会明白这个变量是一个更大结构的一部分。当然，更好的解决方案是创建一个名为 `Address` 的类，这样连编译器也知道这些变量属于一个更大的概念。

### 不要添加无意义的上下文

在一个名为“Gas Station Deluxe”的虚构应用程序中，为每个类添加 `GSD` 前缀是一个坏主意。例如：`GSDAccountAddress`。

较短的名称通常比较长的名称更好，只要它们是清晰的。不要在名称中添加不必要的上下文。

## 第三章 函数

函数是任何主题中的第一层组织。

### 小！！

函数的第一条规则是它们应该很小。函数的第二条规则是它们应该更小。

#### 代码块和缩进

这意味着 `if` 语句、`else` 语句、`while` 语句等中的代码块应该只有一行。这一行可能应该是一个函数调用。这不仅使包含它的函数保持小巧，还增加了文档价值，因为块内调用的函数可以有一个描述性很强的名称。

这也意味着函数不应该大到足以容纳嵌套结构。因此，函数的缩进层级不应超过一层或两层。这当然使函数易于阅读和理解。

### 只做一件事

**函数应该只做一件事。它们应该把这件事做好。它们应该只做这件事。**

#### 函数中的代码块

如果你的函数被划分为多个部分，例如_声明_、_初始化_等，这明显表明函数做了不止一件事。只做一件事的函数无法合理地划分为多个部分。

### 每个函数一个抽象层级

为了确保我们的函数只做“一件事”，我们需要确保函数中的语句都处于相同的抽象层级。

#### 自上而下阅读代码：_逐步向下规则_

我们希望代码像自上而下的叙述一样阅读。我们希望每个函数后面跟着的是下一个抽象层级的函数，这样我们可以在阅读函数列表时，逐步向下阅读，每次下降一个抽象层级。

换句话说，我们希望将程序看作一组 TO 段落，每个段落描述当前的抽象层级，并引用下一个抽象层级的 TO 段落。

> - 要包含设置和拆卸，我们首先包含设置，然后包含测试页面内容，最后包含拆卸。
> - 要包含设置，如果这是一个套件，我们首先包含套件设置，然后包含常规设置。
> - 要包含套件设置，我们在父层次结构中搜索“SuiteSetUp”页面，并添加一个包含该页面路径的 include 语句。
> - 要搜索父层次结构...

事实证明，程序员很难学会遵循这一规则并编写保持单一抽象层级的函数。但学会这一技巧也非常重要。它是保持函数简短并确保它们只做“一件事”的关键。让代码像一组自上而下的 TO 段落一样阅读，是保持抽象层级一致的有效技巧。

### Switch 语句

很难编写一个简短的 switch 语句。即使只有两个 case 的 switch 语句，也比我希望的单个代码块或函数的规模要大。同样，很难编写一个只做一件事的 switch 语句。由于它们的性质，switch 语句总是做 N 件事。不幸的是，我们无法总是避免 switch 语句，但我们可以确保每个 switch 语句都隐藏在低层类中，并且永远不会重复。当然，我们通过多态性来实现这一点。

### 使用描述性名称

> 当每个例程都符合你的预期时，你就知道你正在编写整洁的代码。

实现这一原则的一半工作是为一件事的小函数选择好的名称。函数越小、越专注，就越容易选择一个描述性的名称。

不要害怕使用长名称。一个长的描述性名称比一个短的晦涩名称更好。一个长的描述性名称比一个长的描述性注释更好。使用一种命名约定，使函数名称中的多个单词易于阅读，然后利用这些多个单词为函数命名，以说明它的作用。

选择描述性名称将澄清模块的设计，并帮助你改进它。寻找一个好名称通常会导致代码的有利重构，这并不罕见。

### 函数参数

函数的理想参数数量是零（无参）。其次是一个（单参），紧接着是两个（双参）。应尽可能避免三个参数（三参）。超过三个参数（多参）需要非常特殊的理由——即便如此，也不应使用。

从测试的角度来看，参数更加困难。想象一下编写所有测试用例以确保所有参数组合正常工作的难度。如果没有参数，这很简单。如果有一个参数，这并不太难。有两个参数时，问题变得更具挑战性。超过两个参数时，测试每个适当值的组合可能令人望而生畏。

输出参数比输入参数更难理解。当我们阅读一个函数时，我们习惯于通过参数传入信息并通过返回值传出信息的概念。我们通常不期望信息通过参数传出。因此，输出参数常常让我们感到困惑。

#### 常见的单参形式

传递单个参数到函数中有两个非常常见的原因。你可能是在询问关于该参数的问题，例如 `boolean fileExists(“MyFile”)`。或者你可能是在对该参数进行操作，将其转换为其他内容并返回。例如，`InputStream fileOpen(“MyFile”)` 将文件名 `String` 转换为 `InputStream` 返回值。读者在看到函数时，期望的就是这两种用途。你应该选择能够明确区分这两种用途的名称，并始终在一致的上下文中使用这两种形式。

#### 标志参数

标志参数是丑陋的。将布尔值传递给函数是一种非常糟糕的做法。它立即使方法的签名复杂化，大声宣告该函数做了不止一件事。如果标志为 `true`，它做一件事；如果标志为 `false`，它做另一件事！

#### 双参函数

有两个参数的函数比单参函数更难理解。例如，`writeField(name)` 比 `writeField(output-Stream, name)` 更容易理解。

当然，有时两个参数是合适的。例如，`Point p = new Point(0,0);` 是完全合理的。笛卡尔点自然需要两个参数。

即使是明显的双参函数，如 `assertEquals(expected, actual)`，也是有问题的。你有多少次将实际值放在期望值的位置？这两个参数没有自然的顺序。期望值、实际值的顺序是一种需要练习才能学会的约定。

双参函数并不邪恶，你肯定需要编写它们。然而，你应该意识到它们是有代价的，并应利用可用的机制将它们转换为单参函数。例如，你可以将 `writeField` 方法作为 `outputStream` 的成员，这样你可以说 `outputStream.writeField(name)`。或者你可以将 `outputStream` 作为当前类的成员变量，这样你就不必传递它。或者你可以提取一个新的类，如 `FieldWriter`，在其构造函数中接受 `outputStream`，并有一个 `write` 方法。

#### 三参函数

有三个参数的函数比双参函数更难理解。排序、暂停和忽略的问题增加了一倍多。我建议你在创建三参函数之前非常仔细地考虑。

#### 参数对象

比较：

```java
Circle makeCircle(double x, double y, double radius);
```

与

```java
Circle makeCircle(Point center, double radius);
```

#### 动词和关键词

为函数选择好的名称可以大大有助于解释函数的意图以及参数的顺序和意图。在单参函数的情况下，函数和参数应该形成一个非常好的动词/名词对。例如，`write(name)` 非常有表现力。无论这个“name”是什么，它正在被“写入”。一个更好的名称可能是 `writeField(name)`，它告诉我们这个“name”是一个“字段”。

最后一个是函数名称的关键词形式的一个例子。使用这种形式，我们将参数的名称编码到函数名称中。例如，`assertEquals` 可能更好地写成 `assertExpectedEqualsActual(expected, actual)`。这大大缓解了必须记住参数顺序的问题。

### 输出参数

通常应避免使用输出参数。如果你的函数必须改变某些状态，让它改变其所属对象的状态。

### 命令与查询分离

函数应该要么做什么，要么回答什么，但不要同时做这两件事。你的函数应该改变对象的状态，或者返回关于该对象的一些信息。同时做这两件事通常会导致混淆。

### 优先使用异常而不是返回错误码

从命令函数返回错误码是命令与查询分离的微妙违反。

### 不要重复自己

重复可能是软件中所有邪恶的根源。许多原则和实践都是为了控制或消除它而创建的。

### 结构化编程

一些程序员遵循 Edsger Dijkstra 的结构化编程规则。Dijkstra 说，每个函数以及函数中的每个代码块都应该有一个入口和一个出口。遵循这些规则意味着函数中应该只有一个 `return` 语句，循环中不应该有 `break` 或 `continue` 语句，并且永远不应该有任何 `goto` 语句。

虽然我们对结构化编程的目标和纪律表示同情，但当函数非常小时，这些规则几乎没有好处。只有在较大的函数中，这些规则才能提供显著的好处。

因此，如果你保持函数小巧，那么偶尔的多个 `return`、`break` 或 `continue` 语句不会造成伤害，有时甚至比单一入口、单一出口规则更具表现力。另一方面，`goto` 只在大型函数中有意义，因此应避免使用。

## 第4章 注释

没有什么比恰到好处的注释更有帮助。没有什么比轻率的教条注释更能使模块混乱。没有什么比传播谎言和误导的旧注释更具破坏性。

如果我们的编程语言足够表达力，或者我们有能力巧妙地运用这些语言来表达我们的意图，我们就不需要太多注释——也许根本不需要。

### 注释不能弥补糟糕的代码

清晰且表达力强的代码，即使注释很少，也远胜于杂乱复杂且注释很多的代码。与其花时间写注释来解释你制造的混乱，不如花时间清理这些混乱。

### 用代码解释自己

```java
// 检查员工是否有资格享受全额福利
if ((employee.flags & HOURLY_FLAG) && (employee.age > 65))
```

对比

```java
if (employee.isEligibleForFullBenefits())
```

### 好的注释

有些注释是必要的或有益的。然而，唯一真正好的注释是你找到方法不写的注释。

#### 法律注释

有时我们的公司编码标准迫使我们出于法律原因编写某些注释。例如，版权和作者声明是必要的，并且在每个源文件的开头放入注释中是合理的。

#### 信息性注释

有时提供基本信息的注释是有用的。例如，考虑这个解释抽象方法返回值的注释：

```java
// 返回被测试的 Responder 实例。
protected abstract Responder responderInstance();
```

这样的注释有时可能有用，但最好尽可能使用函数名称来传达信息。例如，在这种情况下，可以通过重命名函数来使注释变得多余：`responderBeingTested`。

#### 意图解释

有时注释不仅仅是提供有关实现的有用信息，还提供了决策背后的意图。例如：

```java
public int compareTo(Object o)
{
  if(o instanceof WikiPagePath)
  {
    WikiPagePath p = (WikiPagePath) o;
    String compressedName = StringUtil.join(names, "");
    String compressedArgumentName = StringUtil.join(p.names, "");
    return compressedName.compareTo(compressedArgumentName);
  }
  return 1; // 我们更大，因为我们是正确的类型。
}
```

#### 澄清

有时将某些晦涩的参数或返回值的含义翻译成可读的内容是有帮助的。通常最好找到一种方法使该参数或返回值本身清晰；但当它是标准库的一部分，或者在你无法更改的代码中时，一个有帮助的澄清注释可能是有用的。

#### 警告后果

有时警告其他程序员某些后果是有用的。

```java
// 除非你有时间可以浪费，否则不要运行。
public void _testWithReallyBigFile() {
  writeLinesToFile(10000000);
  response.setBody(testFile);
  response.readyToSend(this);
  String responseString = output.toString();
  assertSubString("Content-Length: 1000000000", responseString);
  assertTrue(bytesSent > 1000000000);
}
```

#### TODO 注释

有时以 //TODO 注释的形式留下“待办”笔记是合理的。在以下情况下，TODO 注释解释了为什么函数有一个退化的实现以及该函数的未来应该是什么。

```java
//TODO-MdM 这些是不需要的
// 我们希望在实现结账模型时将其删除
protected VersionInfo makeVersion() throws Exception {
  return null;
}
```

TODOs 是程序员认为应该完成但由于某种原因目前无法完成的工作。它可能是删除已弃用功能的提醒，或者是请求其他人查看问题的请求。它可能是请求其他人想出一个更好的名称，或者是提醒进行依赖于计划事件的更改。无论 TODO 是什么，它都不是在系统中留下糟糕代码的借口。

#### 放大

注释可以用来放大某些可能看起来微不足道的事情的重要性。

```java
String listItemContent = match.group(3).trim();
// trim 非常重要。它删除了可能导致项目被识别为另一个列表的起始空格。
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

#### 公共 API 中的 Javadocs

没有什么比一个描述良好的公共 API 更有帮助和令人满意了。标准 Java 库的 Javadocs 就是一个很好的例子。没有它们，编写 Java 程序将非常困难。

### 糟糕的注释

大多数注释都属于这一类。通常它们是糟糕代码的拐杖或借口，或者是对不充分决策的辩解，几乎只是程序员在自言自语。

#### 含糊不清的注释

仅仅因为你觉得自己应该写注释，或者因为流程要求你写注释，就随便写一个注释，这是一种偷懒行为。如果你决定写注释，那么花必要的时间确保它是你能写的最好的注释。例如：

```java
public void loadProperties() {

  try {
    String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
    FileInputStream propertiesStream = new FileInputStream(propertiesPath);
    loadedProperties.load(propertiesStream);
  }
  catch(IOException e) {
    // 没有属性文件意味着所有默认值都已加载
  }
}
```

`catch` 块中的注释是什么意思？显然对作者来说有意义，但它的含义并不那么清晰。显然，如果我们得到一个 `IOException`，这意味着没有属性文件；在这种情况下，所有默认值都会被加载。但是谁加载了所有默认值？

#### 冗余的注释

```java
// 当 this.closed 为 true 时返回的实用方法。如果超时则抛出异常。
public synchronized void waitForClose(final long timeoutMillis) throws Exception {
  if(!closed) {
    wait(timeoutMillis);
    if(!closed)
      throw new Exception("MockResponseSender could not be closed");
  }
}
```

这个注释有什么用？它当然不比代码提供更多信息。它没有为代码辩护，也没有提供意图或理由。它并不比代码更容易阅读。事实上，它比代码更不精确，并诱使读者接受这种不精确性，而不是真正的理解。

#### 误导性注释

有时，尽管有最好的意图，程序员在注释中做出的陈述不够精确，以至于不准确。再考虑一下上一节的例子。该方法并不是在 `this.closed` 变为 `true` 时返回。如果 `this.closed` 是 `true`，它就会返回；否则，它会等待一个盲目的超时，然后如果 `this.closed` 仍然不是 `true`，则抛出异常。

#### 强制要求的注释

规定每个函数都必须有 javadoc，或者每个变量都必须有注释的规则是愚蠢的。这样的注释只会使代码混乱，传播谎言，并导致普遍的混乱和缺乏组织。

```java
/**
*
* @param title CD 的标题
* @param author CD 的作者
* @param tracks CD 上的曲目数
* @param durationInMinutes CD 的时长（分钟）
*/
public void addCD(String title, String author, int tracks, int durationInMinutes) {
  CD cd = new CD();
  cd.title = title;
  cd.author = author;
  cd.tracks = tracks;
  cd.duration = duration;
  cdList.add(cd);
}
```

#### 日志式注释

有时人们每次编辑模块时都会在模块的开头添加注释。例如：

```java
* Changes (from 11-Oct-2001)
* --------------------------
* 11-Oct-2001 : Re-organised the class and moved it to new package com.jrefinery.date (DG);
* 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate class (DG);
* 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate class is gone (DG); Changed getPreviousDayOfWeek(),
getFollowingDayOfWeek() and getNearestDayOfWeek() to correct bugs (DG);
* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
```

今天我们有源代码控制系统，我们不需要这种类型的日志。

#### 噪声注释

以下示例中的注释没有提供新信息。

```java
/**
* 默认构造函数。
*/
protected AnnualDateRule() {
}
```

```java
/** 月份中的某一天。 */
private int dayOfMonth;
```

Javadocs 注释可能属于这一类。很多时候，它们只是冗余的噪声注释，出于某种错误的提供文档的愿望而编写。

#### 当你可以使用函数或变量时，不要使用注释

例如：

```java
// 全局列表 <mod> 中的模块是否依赖于我们所属的子系统？
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

对比

```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

#### 位置标记

这种类型的注释是噪声。

```java
// Actions //////////////////////////////////
```

#### 闭合括号注释

例如：

```java
public class wc {
  public static void main(String[] args) {
    BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
    String line;
    int lineCount = 0;
    int charCount = 0;
    int wordCount = 0;
    try {
      while ((line = in.readLine()) != null) {
        lineCount++;
        charCount += line.length();
        String words[] = line.split("\\W");
        wordCount += words.length;

      } //while
      System.out.println("wordCount = " + wordCount);
      System.out.println("lineCount = " + lineCount);
      System.out.println("charCount = " + charCount);

    } // try
    catch (IOException e) {
      System.err.println("Error:" + e.getMessage());

    } //catch

  } //main
```

你可以将代码拆分为小函数，而不是使用这种类型的注释。

#### 署名和作者信息

例如：

`/* 由 Rick 添加 */`

版本控制系统可以管理这些信息。

#### 注释掉的代码

```java
InputStreamResponse response = new InputStreamResponse();
response.setBody(formatter.getResultStream(), formatter.getByteCount());
// InputStream resultsStream = formatter.getResultStream();
// StreamReader reader = new StreamReader(resultsStream);
// response.setContent(reader.read(formatter.getByteCount()));
```

如果你不再需要它，请删除它，如果需要，你可以稍后通过版本控制系统找回它。

#### HTML 注释

源代码注释中的 HTML 是一种令人厌恶的东西，正如你从下面的代码中可以看出。

```java
/**
* Task to run fit tests.
* This task runs fitnesse tests and publishes the results.
* <p/>
* <pre>
* Usage:
* &lt;taskdef name=&quot;execute-fitnesse-tests&quot;
* classname=&quot;fitnesse.ant.ExecuteFitnesseTestsTask&quot;
* classpathref=&quot;classpath&quot; /&gt;
* OR
* &lt;taskdef classpathref=&quot;classpath&quot;
* resource=&quot;tasks.properties&quot; /&gt;
* <p/>
* &lt;execute-fitnesse-tests
* suitepage=&quot;FitNesse.SuiteAcceptanceTests&quot;
* fitnesseport=&quot;8082&quot;
* resultsdir=&quot;${results.dir}&quot;
* resultshtmlpage=&quot;fit-results.html&quot;
* classpathref=&quot;classpath&quot; /&gt;
* </pre>
*/
```

#### 非本地信息

如果你必须写注释，那么确保它描述了它附近的代码。不要在本地注释的上下文中提供系统范围的信息。

#### 过多的信息

不要将有趣的历史讨论或无关的细节描述放入你的注释中。

#### 不明显的联系

注释和它描述的代码之间的联系应该是显而易见的。如果你打算写注释，那么至少你希望读者能够查看注释和代码，并理解注释在说什么。

#### 函数头

短函数不需要太多描述。为一个小函数选择一个好名字通常比注释头更好。

#### 非公共代码中的 Javadocs

Javadocs 适用于公共 API，在非公共代码中可能是一种干扰，而不是帮助。

## 第5章 格式化

代码格式化很重要。它太重要了，不能忽视，也不能过于教条地对待。代码格式化是关于沟通的，而沟通是专业开发者的首要任务。

### 垂直格式化

#### 概念之间的垂直开放性

这个概念涉及如何在代码中分隔概念。在下面的示例中，我们可以看到这一点。

```java
package fitnesse.wikitext.widgets;

import java.util.regex.*;

public class BoldWidget extends ParentWidget {
  public static final String REGEXP = "'''.+?'''";
  private static final Pattern pattern = Pattern.compile("'''(.+?)'''",
      Pattern.MULTILINE + Pattern.DOTALL
      );

  public BoldWidget(ParentWidget parent, String text) throws Exception {
    super(parent);
    Matcher match = pattern.matcher(text);
    match.find();
    addChildWidgets(match.group(1));
  }

  public String render() throws Exception {
    StringBuffer html = new StringBuffer("<b>");
    html.append(childHtml()).append("</b>");
    return html.toString();
  }
}
```

```java
package fitnesse.wikitext.widgets;
import java.util.regex.*;
public class BoldWidget extends ParentWidget {
  public static final String REGEXP = "'''.+?'''";
  private static final Pattern pattern = Pattern.compile("'''(.+?)'''",
  Pattern.MULTILINE + Pattern.DOTALL);
  public BoldWidget(ParentWidget parent, String text) throws Exception {
    super(parent);
    Matcher match = pattern.matcher(text); match.find(); addChildWidgets(match.group(1));
  }
  public String render() throws Exception { StringBuffer html = new StringBuffer("<b>"); html.append(childHtml()).append("</b>"); return html.toString();
  }
}
```

正如你所看到的，第一个示例的可读性比第二个更高。

#### 垂直密度

垂直密度意味着紧密的关联。因此，紧密相关的代码行应该在垂直方向上紧凑排列。查看以下示例：

```java
public class ReporterConfig {

  /**
   * The class name of the reporter listener */
  private String m_className;

  /**
   * The properties of the reporter listener */
  private List<Property> m_properties = new ArrayList<Property>();

  public void addProperty(Property property) { m_properties.add(property);
}
```

```java
public class ReporterConfig {
  private String m_className;
  private List<Property> m_properties = new ArrayList<Property>();

  public void addProperty(Property property) {
    m_properties.add(property);
  }
}
```

第二个代码更容易阅读。它一目了然。

#### 垂直距离

**变量声明**。变量应尽可能靠近它们的使用位置声明。因为我们的函数非常短，局部变量应出现在每个函数的顶部。

**实例变量**，另一方面，应声明在类的顶部。这不应增加这些变量的垂直距离，因为在一个设计良好的类中，它们被许多（如果不是全部）方法使用。

关于实例变量的位置有很多争论。在 C++ 中，我们通常遵循所谓的剪刀规则，将所有实例变量放在底部。然而，在 Java 中，常见的约定是将它们全部放在类的顶部。我认为没有理由遵循其他约定。重要的是实例变量应在一个众所周知的地方声明。每个人都应该知道去哪里查看声明。

**相关函数**。如果一个函数调用另一个函数，它们应该在垂直方向上靠近，并且调用者应尽可能位于被调用者的上方。这为程序提供了一个自然的流程。如果这个约定被可靠地遵循，读者将能够相信函数定义会在使用后不久出现。

**概念亲和性**。某些代码片段希望靠近其他代码片段。它们具有某种概念亲和性。这种亲和性越强，它们之间的垂直距离应越小。

#### 垂直顺序

通常我们希望函数调用依赖关系指向下方。也就是说，被调用的函数应位于调用函数的下方。这为源代码模块创建了一个从高级到低级的自然流程。_（这与 Pascal、C 和 C++ 等语言完全相反，这些语言要求函数在使用之前定义或至少声明）_

### 水平格式化

#### 水平开放性和密度

我们使用水平空白来关联强相关的事物，并分离弱相关的事物。例如：

```java
private void measureLine(String line) {
  lineCount++;
  int lineSize = line.length();
  totalChars += lineSize;
  lineWidthHistogram.addLine(lineSize, lineCount);
  recordWidestLine(lineSize);
}
```

赋值语句有两个明显且主要的元素：左边和右边。空格使这种分离显而易见。

#### 水平对齐

```java
public class Example implements Base
{
  private   Socket      socket;
  private   inputStream input;
  protected long        requestProgress;

  public Expediter(Socket      s,
                   inputStream input) {
    this.socket =     s;
    this.input  =     input;
  }
}
```

在现代语言中，这种对齐方式并不有用。对齐似乎强调了错误的内容，并将我的注意力从真正的意图上引开。

```java
public class Example implements Base
{
  private Socket socket;
  private inputStream input;
  protected longrequestProgress;

  public Expediter(Socket s, inputStream input) {

    this.socket = s;
    this.input = input;
  }
}
```

这是一个更好的方法。

### 缩进

缩进很重要，因为它帮助我们拥有可见的层次结构和定义良好的块。

### 团队规则

每个程序员都有自己喜欢的格式化规则，但如果他在团队中工作，那么团队规则优先。

开发团队应就一种格式化风格达成一致，然后团队的每个成员都应使用这种风格。我们希望软件具有一致的风格。我们不希望它看起来是由一群意见不合的个人编写的。

## 第6章 对象和数据结构

### 数据抽象

隐藏实现不仅仅是简单地在变量之间放置一层函数。隐藏实现是关于抽象的！一个类不仅仅是通过 getter 和 setter 将变量暴露出来。相反，它暴露了允许用户操作数据本质的抽象接口，而无需了解其实现。

### 数据/对象的反对称性

这两个示例展示了对象和数据结构之间的区别。对象将其数据隐藏在抽象后面，并暴露操作这些数据的函数。数据结构暴露其数据，并且没有有意义的函数。

**过程式形状**

```java
public class Square {
  public Point topLeft;
  public double side;
}

public class Rectangle {
  public Point topLeft;
  public double height;
  public double width;
}

public class Circle {
  public Point center;
  public double radius;
}

public class Geometry {
  public final double PI = 3.141592653589793;

  public double area(Object shape) throws NoSuchShapeException {
    if (shape instanceof Square) {
      Square s = (Square)shape;
      return s.side * s.side;
    }
    else if (shape instanceof Rectangle) { Rectangle r = (Rectangle)shape; return r.height * r.width;
    }
    else if (shape instanceof Circle) {
      Circle c = (Circle)shape;
      return PI * c.radius * c.radius;
    }
    throw new NoSuchShapeException();
  }
}
```

**多态形状**

```java
public class Square implements Shape {
  private Point topLeft;
  private double side;

  public double area() {
    return side*side;
  }
}

public class Rectangle implements Shape {
  private Point topLeft;
  private double height;
  private double width;

  public double area() {
    return height * width;
  }
}

public class Circle implements Shape {
  private Point center;
  private double radius;
  public final double PI = 3.141592653589793;

  public double area() {
    return PI * radius * radius;
  }
}
```

再次，我们看到了这两种定义的互补性；它们几乎是相反的！这揭示了对象和数据结构之间的根本二分法：

> 过程式代码（使用数据结构的代码）使得在不改变现有数据结构的情况下添加新函数变得容易。而面向对象代码使得在不改变现有函数的情况下添加新类变得容易。

反之亦然：

> 过程式代码使得添加新数据结构变得困难，因为所有函数都必须更改。面向对象代码使得添加新函数变得困难，因为所有类都必须更改。

成熟的程序员知道，一切都是对象的想法是一个神话。有时你真的只想要简单的数据结构和操作它们的函数。

### [德米特法则](https://en.wikipedia.org/wiki/Law_of_Demeter)

有一个众所周知的启发式法则叫做德米特法则，它说一个模块不应该知道它操作的对象的内部结构。

更准确地说，德米特法则说，类 `C` 的方法 `f` 应该只调用以下对象的方法：

- `C`
- 由 `f` 创建的对象
- 作为参数传递给 `f` 的对象
- `C` 的实例变量持有的对象

该方法不应调用由任何允许函数返回的对象的方法。换句话说，与朋友交谈，而不是与陌生人交谈。

### 数据传输对象

数据结构的典型形式是一个具有公共变量且没有函数的类。这有时被称为数据传输对象（DTO）。DTO 是非常有用的结构，特别是在与数据库通信或解析来自套接字的消息时。它们通常成为将数据库中的原始数据转换为应用程序代码中的对象的一系列翻译阶段中的第一步。

## 第7章 错误处理

许多代码库完全被错误处理所主导。当我说主导时，我并不是说错误处理是它们所做的全部。我的意思是，由于所有分散的错误处理，几乎不可能看到代码的功能。错误处理很重要，但如果它掩盖了逻辑，那就是错误的。

### 使用异常而不是返回错误码

在遥远的过去，有许多语言没有异常。在这些语言中，处理和报告错误的技术是有限的。你要么设置一个错误标志，要么返回一个调用者可以检查的错误码。

### 首先编写 Try-Catch-Finally 语句

在某种程度上，try 块就像事务。无论 try 块中发生什么，你的 catch 都必须使程序保持一致状态。因此，在编写可能抛出异常的代码时，最好从 try-catch-finally 语句开始。这有助于你定义该代码的用户应该期望什么，无论 try 中执行的代码出了什么问题。

### 提供异常的上下文

你抛出的每个异常都应提供足够的上下文，以确定错误的来源和位置。

创建信息丰富的错误消息，并将其与异常一起传递。提及失败的操作和失败的类型。如果你在应用程序中记录日志，请传递足够的信息以便在 catch 中记录错误。

### 不要返回 null

如果你倾向于从方法返回 null，请考虑抛出异常或返回一个特殊情况的对象。如果你从第三方 API 调用返回 null 的方法，请考虑将该方法包装在一个抛出异常或返回特殊情况对象的方法中。

### 不要传递 null

从方法返回 null 是不好的，但将 null 传递给方法更糟糕。除非你使用的 API 期望你传递 null，否则你应该尽可能避免在代码中传递 null。

## 第8章 边界

我们很少控制我们系统中的所有软件。有时我们购买第三方包或使用开源软件。其他时候，我们依赖公司内部的团队为我们生产组件或子系统。无论如何，我们必须将这些外部代码与我们自己的代码干净地集成。

### 使用第三方代码

接口提供者和接口使用者之间存在一种天然的张力。第三方包和框架的提供者努力追求广泛的适用性，以便它们可以在许多环境中工作并吸引广泛的受众。另一方面，用户希望接口专注于他们的特定需求。这种张力可能会在我们系统的边界上引起问题。例如：

```java
Map sensors = new HashMap();
Sensor s = (Sensor)sensors.get(sensorId);
```

对比

```java
public class Sensors {
  private Map sensors = new HashMap();

  public Sensor getById(String id) {
    return (Sensor) sensors.get(id);
  }
  //snip
}
```

第一个代码暴露了 Map 中的强制类型转换，而第二个代码能够以对应用程序其余部分影响很小的方式演进。强制类型转换和类型管理在 Sensors 类内部处理。

接口也被定制和约束以满足应用程序的需求。这导致代码更易于理解且更难以误用。Sensors 类可以强制执行设计和业务规则。

### 探索和学习边界

第三方代码帮助我们在更短的时间内交付更多功能。当我们想利用一些第三方包时，我们从哪里开始？测试第三方代码不是我们的工作，但为我们使用的第三方代码编写测试可能符合我们的最佳利益。

编写一些测试来学习和理解如何使用第三方代码是一个好主意。Newkirk 称这种测试为学习测试。

### 学习测试比免费更好

学习测试最终不会花费任何成本。我们无论如何都要学习 API，而编写这些测试是获得这些知识的一种简单且隔离的方式。学习测试是精确的实验，有助于增加我们的理解。

学习测试不仅是免费的，它们还具有积极的投资回报。当第三方包有新版本时，我们运行学习测试以查看是否存在行为差异。

### 使用尚未存在的代码

有时有必要在一个模块上工作，该模块将连接到另一个正在开发的模块，而我们不知道如何发送信息，因为 API 尚未设计。在这种情况下，建议创建一个接口来封装与待定模块的通信。这样，我们可以保持对我们模块的控制，并且即使第二个模块尚不可用，我们也可以进行测试。

### 保持清晰的边界

在边界处经常会发生一些有趣的事情。其中不乏行为的变化。好的软件设计应该能够在不需要巨大投入和重构的情况下适应变化。当使用不受我们控制的代码时，必须特别注意保护我们的投资，确保未来的变更不会代价太大。

## 第九章 单元测试

- **T**est：测试代码
- **D**riven：驱动生产代码
- **D**evelopment：开发

### TDD 的三条法则

- **第一条法则** 在编写失败的单元测试之前，你不能编写生产代码。
- **第二条法则** 你不能编写比足以失败的单元测试更多的代码，而不编译就是失败。
- **第三条法则** 你不能编写比足以通过当前失败测试的生产代码更多的代码。

### 干净的测试

如果你不保持测试的干净，你将失去它们。

可读性对于保持测试的干净非常重要。

### 每个测试一个断言

建议每个测试只维护一个断言，因为这有助于保持每个测试易于理解。

### 每个测试一个概念

这条规则将帮助你保持函数简短。

- **为你需要验证的每个概念编写一个测试**

### F.I.R.S.T

- **快速** 测试应该快速。
- **独立** 测试不应该相互依赖。
- **可重复** 测试应该在任何环境中可重复。
- **自验证** 测试应该有一个布尔输出。它们要么通过，要么失败。
- **及时** 单元测试应该在使它们通过的生产代码之前编写。如果你在生产代码之后编写测试，那么你可能会发现生产代码难以测试。

## 第十章 类

## 类的组织

### 封装

我们喜欢保持变量和工具函数小巧，但我们并不狂热。有时我们需要将变量或工具函数设置为受保护的，以便测试可以访问它们。

## 类应该小巧

- 第一条规则：类应该小巧
- 第二条规则：**类应该比第一条规则更小**

### 单一职责原则

**类应该有一个职责——一个改变的理由**

单一职责原则（SRP）是面向对象设计中更重要的概念之一。它也是最容易理解和遵守的概念之一。

### 内聚性

类应该具有少量的实例变量。类的每个方法都应该操作这些变量中的一个或多个。一般来说，一个方法操作的变量越多，该方法与类的内聚性就越强。一个类中每个变量都被每个方法使用时，该类具有最大的内聚性。

### 保持内聚性会导致许多小类

仅仅将大函数拆分为小函数的行为就会导致类的激增。

## 为变化而组织

对于大多数系统来说，变化是持续的。每次变化都会使我们面临系统其余部分不再按预期工作的风险。在一个干净的系统中，我们组织类以减少变化的风险。

### 隔离变化

需求会变化，因此代码也会变化。我们在面向对象基础中学到，有具体类（包含实现细节的代码）和抽象类（仅表示概念）。依赖于具体细节的客户端类在这些细节变化时面临风险。我们可以引入接口和抽象类来帮助隔离这些细节的影响。

## 第11章 系统

## 将系统构建与使用分离

_软件系统应该将启动过程（当应用程序对象被构建且依赖项被“连接”在一起时）与启动后接管运行的运行时逻辑分开_

### 与 main 分离

将构建与使用分离的一种简单方法是将构建的所有方面移到 `main` 或由 `main` 调用的模块中，并设计系统的其余部分，假设所有对象都已正确创建和连接。

抽象工厂模式是这种方法的一个选择。

### 依赖注入

依赖注入（DI）是将构建与使用分离的强大机制，它是控制反转（IoC）在依赖管理中的应用。控制反转将次要职责从对象转移到专门用于此目的的其他对象，从而支持单一职责原则。在依赖管理的上下文中，对象不应负责实例化其依赖项。相反，它应该将此责任传递给另一个“权威”机制，从而反转控制。由于设置是一个全局关注点，这个权威机制通常是“main”例程或特殊用途的_容器_。

## 第12章 涌现

根据 Kent Beck 的说法，如果设计遵循以下规则，那么它就是“简单”的：

- 运行所有测试
- 不包含重复
- 表达程序员的意图
- 最小化类和方法的数量

## 第13章 并发

并发是一种解耦策略。它帮助我们解耦“做什么”和“何时做”。在单线程应用程序中，“做什么”和“何时做”是如此紧密地耦合在一起，以至于通常可以通过查看堆栈回溯来确定整个应用程序的状态。调试此类系统的程序员可以设置断点或一系列断点，并通过命中哪些断点来了解系统的状态。

将“做什么”与“何时做”解耦可以显著提高应用程序的吞吐量和结构。从结构的角度来看，应用程序看起来像许多协作的小计算机，而不是一个大主循环。这可以使系统更容易理解，并提供一些强大的方法来分离关注点。

## 神话和误解

- 并发总是提高性能。
  并发有时可以提高性能，但只有在有大量等待时间可以在多个线程或多个处理器之间共享时。这两种情况都不简单。
- 编写并发程序时设计不会改变。
  事实上，并发算法的设计与单线程系统的设计可能有显著不同。“做什么”与“何时做”的解耦通常对系统的结构有巨大影响。
- 在使用诸如 Web 或 EJB 容器时，理解并发问题并不重要。
  事实上，你最好知道你的容器在做什么，以及如何防范本章后面描述的并发更新和死锁问题。
  以下是关于编写并发软件的一些更平衡的观点：
- 并发会带来一些开销，无论是在性能上还是在编写额外代码上。
- 正确的并发是复杂的，即使对于简单的问题也是如此。
- 并发错误通常不可重复，因此它们通常被忽略为一次性问题，而不是它们真正的缺陷。
- 并发通常需要设计策略的根本性改变。

## 第14章 逐步改进

本章是一个案例研究。建议完整阅读以更好地理解。

## 第15章 JUnit 内部

本章分析了 JUnit 工具。建议完整阅读以更好地理解。

## 第16章 重构 SerialDate

本章是一个案例研究。建议完整阅读以更好地理解。

## 第17章 代码风格和启发式方法

这是来自 Martin Fowler 的《重构》和 Robert C Martin 的《代码整洁之道》的代码风格参考。

虽然整洁的代码来自于纪律而不是列表或价值体系，但这里是一个起点。

## 总结

### 注释

#### C1: 不恰当的信息

保留注释用于引用代码和设计的技术说明。

#### C2: 过时的注释

更新或删除过时的注释。

#### C3: 冗余的注释

冗余的注释描述了能够充分自我描述的内容。

#### C4: 写得不好的注释

注释应简洁、简明、拼写正确。

#### C5: 注释掉的代码

幽灵代码。删除它。

### 环境

#### E1: 构建需要多于一步

构建应该只需要一个命令来检出和一个命令来运行。

#### E2: 测试需要多于一步

测试应该通过 IDE 的一个按钮点击运行，或者通过一个命令运行。

### 函数

#### F1: 过多的参数

函数的参数应该从零开始，然后是一个，接着是两个，然后是三个。不要超过三个。

#### F2: 输出参数

参数是输入，而不是输出。如果必须改变某些状态，让它成为被调用对象的状态。

#### F3: 标志参数

消除布尔参数。

#### F4: 死函数

丢弃未调用的方法。这是死代码。

### 通用

#### G1: 一个源文件中的多种语言

尽量减少源文件中的语言数量。理想情况下，只有一种。

#### G2: 未实现显而易见的行为

函数或类的结果不应令人惊讶。

#### G3: 边界条件下的错误行为

为每个边界条件编写测试。

#### G4: 覆盖安全措施

覆盖安全措施并施加手动控制会导致代码崩溃。

#### G5: 重复

对重复代码进行抽象。用多态替换重复的函数。

#### G6: 代码处于错误的抽象层次

确保抽象代码被分离到不同的容器中。

#### G7: 基类依赖于它们的派生类

实践模块化。

#### G8: 过多的信息

用少量的代码做大量的事情。限制类或函数中发生的事情的数量。

#### G9: 死代码

删除未执行的代码。

#### G10: 垂直分离

在调用它们的地方附近定义变量和函数。

#### G11: 不一致

选择一个约定，并遵循它。记住不要有意外。

#### G12: 混乱

死代码。

#### G13: 人为耦合

偏爱清晰的代码，而不是方便的代码。不要将偏爱心理映射而不是清晰性的代码分组。

#### G14: 特性嫉妒

一个类的方法不应与另一个类的方法纠缠在一起。

#### G15: 选择器参数

不要在函数末尾炫耀虚假参数。

#### G16: 模糊的意图

代码不应是魔法或模糊的。

#### G17: 错误放置的责任

使用清晰的函数名称作为代码放置的路标。

#### G18: 不恰当的静态

使你的函数非静态。

#### G19: 使用解释性变量

创建解释性变量，并且要有很多。

#### G20: 函数名称应说明它们的作用

...

#### G21: 理解算法

理解函数的工作原理。通过测试是不够的。重构函数可以导致对其更好的理解。

#### G22: 使逻辑依赖物理化

理解你的代码在做什么。

#### G23: 优先使用多态而不是 If/Else 或 Switch/Case

避免使用 switch/case 的蛮力。

#### G24: 遵循标准约定

你的团队的约定是什么并不重要。重要的是你有一个并且每个人都遵循它。

#### G25: 用命名常量替换魔法数字

停止拼写数字。

#### G26: 精确

不要懒惰。考虑可能的结果，然后覆盖并测试它们。

#### G27: 结构优于约定

设计决策应具有结构而不是教条。

#### G28: 封装条件

使你的条件更精确。

#### G29: 避免否定条件

否定条件比肯定条件需要更多的脑力来理解。

#### G31: 隐藏的时间耦合

使用使时间耦合显式的参数。

#### G32: 不要随意

你的代码结构应传达其结构的原因。

#### G33: 封装边界条件

避免将 +1 和 -1 泄漏到你的代码中。

#### G34: 函数应只下降一个抽象层次

最难遵循的启发式方法。函数描述的操作下方的一个抽象层次可以帮助澄清你的代码。

#### G35: 将可配置数据保持在高层

高层常量易于更改。

#### G36: 避免传递导航

编写害羞的代码。模块应只了解它们的邻居，而不是邻居的邻居。

### 命名

#### N1: 选择描述性名称

选择描述性和相关的名称。

#### N2: 在适当的抽象层次选择名称

考虑在不同程序中使用时仍然对用户清晰的名称。

#### N3: 尽可能使用标准命名法

使用表达其任务的名称。

#### N4: 明确的名称

偏爱清晰性而不是简洁性。一个长而富有表现力的名称比一个短而乏味的名称更好。

#### N5: 在长作用域中使用长名称

名称的长度应与其作用域相关。

#### N6: 避免编码

不要在名称中编码类型或作用域信息。

#### N7: 名称应描述副作用

考虑函数的副作用，并将其包含在名称中。

### 测试

#### T1: 测试不足

测试所有可能出错的地方。

#### T2: 使用覆盖率工具！

使用你的 IDE 作为覆盖率工具。

#### T3: 不要跳过琐碎的测试

...

#### T4: 被忽略的测试是对模糊性的疑问

如果你的测试被忽略，代码就会受到质疑。

#### T5: 测试边界条件

中间通常被覆盖。记住边界。

#### T6: 彻底测试靠近错误的地方

错误很少是孤立的。当你找到一个时，在附近寻找另一个。

#### T7: 失败的模式是揭示性的

有序的测试用例将揭示失败的模式。

#### T8: 测试覆盖率模式可以是揭示性的

同样，查看在失败中通过或未通过的代码。

#### T9: 测试应该快速

慢的测试不会被执行。
