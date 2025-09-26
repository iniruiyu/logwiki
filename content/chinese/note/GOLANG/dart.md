---
title: "Dart基础知识"
meta_title: ""
description: "Dart基础知识"
date: 2025-05-21T05:00:00Z
image: "/images/gallery/01.jpg"
categories: ["dart", "golang", "flutter"]
author: "ruiyu"
tags: ["dart", "flutter", "golang"]
draft: false
---



# 1. 变量 

## **一、变量声明基础**

| **方式**                 | **示例**                | **关键说明**                                |
| ------------------------ | ----------------------- | ------------------------------------------- |
| **`var`（推荐）**        | `var name = 'Bob';`     | 优先使用！编译器自动推断类型（局部变量）    |
| **显式类型**             | `String name = 'Bob';`  | 类成员/函数参数建议用显式类型（提高可读性） |
| **`Object`（通用类型）** | `Object name = 'Bob';`  | 不能直接调用子类型方法（需转换）            |
| **`dynamic`（慎用）**    | `dynamic name = 'Bob';` | 跳过类型检查（仅用于动态数据如JSON）        |

> 💡 **重点**：局部变量 **优先用 `var`**（符合Dart风格指南）。

------

## **二、空安全（Null Safety）**

**核心规则**：**禁止运行时 `null` 错误** → 编译器提前报错！

| **类型**                      | **示例**               | **关键规则**                                     |
| ----------------------------- | ---------------------- | ------------------------------------------------ |
| **非空类型**（不可为 `null`） | `String name = 'Bob';` | **必须初始化**（编译器强制）                     |
| **可空类型**（可为 `null`）   | `String? name = null;` | 末尾加 `?`，默认初始化为 `null`                  |
| **访问限制**                  | `name.length`          | **不能直接调用可空变量的方法**（除非 `as` 转换） |

> ✅ **正确用法**：
>
> ```dart
> String? name = null;
> print(name?.length); // 安全访问（?.：空安全操作符）
> ```

------

## **三、`late` 修饰符（延迟初始化）**

**用途**：声明 **非空变量但不在初始化时赋值**（Dart 无法自动检测初始化时机时使用）

```dart
late String description; // 未初始化，但必须在使用前赋值
void main() {
  description = 'Feijoada!'; // 必须赋值
  print(description);
}
```

> ⚠️ **注意**：若未初始化就使用 → **运行时错误**（`LateInitializationError`）。

------

## **四、`final` 与 `const`（不可变变量）**

| **修饰符** | **初始化时机** | **可变性**                  | **适用场景**                 |
| ---------- | -------------- | --------------------------- | ---------------------------- |
| `final`    | 运行时（一次） | **引用不可变**（内容可变）  | 实例变量/运行时值            |
| `const`    | 编译时（常量） | **完全不可变**（内容+引用） | 编译时常量（数字、字符串等） |

> ✅ **对比示例**：
>
> ```dart
> final name = 'Bob'; // 运行时赋值，引用不可变
> name = 'Alice'; // ❌ 错误：final 只能赋值一次
> 
> const pi = 3.14; // 编译时常量
> const list = [1, 2, 3]; // 不可变列表
> list.add(4); // ❌ 错误：const 数组不可变
> ```

> 💡 **关键区别**：
>
> - `final` 对象的**字段可变**（如 `final list = [1,2]` → `list.add(3)` ✅）
> - `const` 对象**完全不可变**（字段+引用均不可变）

------

##  **五、其他重点**

1. **默认值**

   - 可空变量（`String?`）默认值 = `null`
   - 非空变量（`String`）**必须初始化**（否则编译报错）

   ```dart
   int? count; // 默认 null
   int count = 0; // 必须初始化
   ```

2. **`_`（通配符变量）**

   - 仅作占位符（值不可访问）

   ```dart
   for (var _ in [1,2,3]) {} // 无需变量名
   try { ... } catch (_) {} // 忽略异常
   ```

3. **空安全例外**

   - `toString()` 和 `hashCode` **支持 `null`**（`null.toString()` 返回 `'null'`）
   - 但其他方法（如 `.length`）**不支持** → 必须用 `?.` 或 `as` 转换。

------

##  **速查表：变量使用规范**

| **场景**         | **推荐写法**           | **错误写法**            |
| ---------------- | ---------------------- | ----------------------- |
| 局部变量（推荐） | `var name = 'Bob';`    | `String name = 'Bob';`  |
| 可空类型         | `String? name = null;` | `String name = null;`   |
| 运行时不可变     | `final name = 'Bob';`  | `var name = 'Bob';`     |
| 编译时常量       | `const pi = 3.14;`     | `final pi = 3.14;`      |
| 避免 `dynamic`   | `String name = 'Bob';` | `dynamic name = 'Bob';` |

------

> ✅ **总结口诀**：
>  **`var` 优先局部用，`?` 标明可为空，**
>  **`final` 一次赋值，`const` 编译常量，**
>  **`late` 延迟初始化，`_` 通配符占位。**



# 2.操作符

##  **一、操作符优先级与结合性（从高到低）**

| **类别**           | **操作符**                                                  | **结合性** |
| ------------------ | ----------------------------------------------------------- | ---------- |
| **一元后缀**       | `expr++`, `expr--`, `()`, `[]`, `?[]`, `.`, `?.`, `!`       | 无         |
| **一元前缀**       | `-expr`, `!expr`, `~expr`, `++expr`, `--expr`, `await expr` | 无         |
| **乘除**           | `*`, `/`, `%`, `~/`                                         | 左         |
| **加减**           | `+`, `-`                                                    | 左         |
| **位移**           | `<<`, `>>`, `>>>`                                           | 左         |
| **位运算**         | `&`, `^`, `                                                 | `          |
| **关系与类型检查** | `>=`, `>`, `<=`, `<`, `as`, `is`, `is!`                     | 无         |
| **相等性**         | `==`, `!=`                                                  | 无         |
| **逻辑与**         | `&&`                                                        | 左         |
| **逻辑或**         | `                                                           |            |
| **空安全赋值**     | `??`                                                        | 左         |
| **条件表达式**     | `expr1 ? expr2 : expr3`                                     | 右         |
| **级联操作**       | `..`, `?..`                                                 | 左         |
| **赋值**           | `=`, `*=`, `/=`, `+=`, `-=`, `&=`, `^=`, 等                 | 右         |
| **展开操作**       | `...`, `...?`                                               | 无         |

> ✅ "expr"是"expression"（表达式）的缩写，是一个**通用占位符**
>
> **优先级记忆口诀**：
>  **一元 > 乘除 > 加减 > 位移 > 位运算 > 关系/类型 > 相等 > 逻辑 > 条件 > 级联/赋值**

## 1. **算术操作符**

| **操作符** | **含义**              | **示例**                 |
| ---------- | --------------------- | ------------------------ |
| `+`        | 加法                  | `2 + 3 == 5`             |
| `-`        | 减法                  | `5 - 2 == 3`             |
| `*`        | 乘法                  | `2 * 3 == 6`             |
| `/`        | 除法（返回 `double`） | `5 / 2 == 2.5`           |
| `~/`       | 整除                  | `5 ~/ 2 == 2`            |
| `%`        | 取模                  | `5 % 2 == 1`             |
| `++`/`--`  | 自增/自减             | `var a = 0; a++; // a=1` |

> ⚠️ **注意**：
>
> - `var a = 0; b = a++;` → `b=0`（后缀自增：先赋值后加1）
> - `var a = 0; b = ++a;` → `b=1`（前缀自增：先加1后赋值）

------

## 2. **比较操作符**

| **操作符** | **含义** | **示例**        |
| ---------- | -------- | --------------- |
| `==`       | 等于     | `2 == 2 → true` |
| `!=`       | 不等于   | `2 != 3 → true` |
| `>`        | 大于     | `3 > 2 → true`  |
| `<`        | 小于     | `2 < 3 → true`  |
| `>=`       | 大于等于 | `3 >= 3 → true` |
| `<=`       | 小于等于 | `2 <= 3 → true` |

> ✅ **对象比较**：
>
> ```dart
> obj1 == obj2; // 调用对象的 `==` 方法  
> identical(obj1, obj2); // 判断是否是同一个对象（内存地址相同）
> ```



#### 3. **类型检查与类型转换**

| **操作符** | **含义**     | **示例**               |
| ---------- | ------------ | ---------------------- |
| `is`       | 类型检查     | `if (x is String) {}`  |
| `is!`      | 非类型检查   | `if (x is! int) {}`    |
| `as`       | 强制类型转换 | `(x as String).length` |

> ⚠️ **安全转换**：
>
> ```dart
> if (x is String) { 
>   print(x.length); // 安全访问 String 方法
> }
> ```



# 3.注释

## **Dart 注释类型速查表**

| **类型**     | **语法**              | **关键规则**                                                 | **示例**                                             |
| ------------ | --------------------- | ------------------------------------------------------------ | ---------------------------------------------------- |
| **单行注释** | `//`                  | 编译器忽略 `//` 后到行末的所有内容（**不可嵌套**）           | `// TODO: 优化逻辑`                                  |
| **多行注释** | `/* ... */`           | 编译器忽略 `/*` 和 `*/` 之间的内容（**支持嵌套**）           | `/* 这是多行注释<br>可以跨行 */`                     |
| **文档注释** | `///` 或 `/** ... */` | **生成 API 文档**，`[引用]` 会自动链接到类/方法（如 `[feed]` → `feed()` 方法） | `/// 饲喂羊驼 [food]` `void feed(Food food) { ... }` |

------

##  **关键规则总结**

1. **文档注释的引用规则**

   - 用 `[名称]` 引用代码元素（自动转为链接）
     → `[feed]` → `feed()` 方法，`[Food]` → `Food` 类
   - **必须在文档注释中**（普通注释 `//` 或 `/* */` 无效）

2. **多行注释嵌套**

   ```dart
   /* 这是外层注释
      /* 这是内层注释 */  // ✅ Dart 允许嵌套
   */
   ```

3. **文档注释的生成**

   - 用 `dart doc` 生成 HTML 文档（如 Dart API 文档）
   - **推荐**：所有公开 API 必须添加文档注释（符合 高效 Dart 指南）

------

##  **文档注释示例（直接可用）**

```dart
/// 一只驯化的南美骆驼科动物（*Lama glama*）。
///
/// 安第斯文化自史前时期就将羊驼用于肉类和驮运。
///
/// 羊驼需要进食，别忘了用 [food] 饲喂它们。
class Llama {
  String? name;

  /// 饲喂羊驼 [food]。
  ///
  /// 羊驼每周典型食量：1捆干草。
  void feed(Food food) { ... }

  /// 用 [activity] 活动锻炼羊驼 [timeLimit] 分钟。
  void exercise(Activity activity, int timeLimit) { ... }
}
```

> ✅ 生成文档效果：
>  `喂食羊驼 [food]` → `[food]` 会变成链接指向 `feed()` 方法
>  `用 [Food] 饲喂` → `[Food]` 会变成链接指向 `Food` 类

------

###  **常见错误**

| **错误写法**                                  | **问题**                        | **正确写法**               |
| --------------------------------------------- | ------------------------------- | -------------------------- |
| `// [feed]`                                   | 单行注释无法生成链接            | `/// [feed]`               |
| `/* [food] */`                                | 多行注释未用 `///` 无法生成链接 | `/// [food]`               |
| `void feed(Food food) { ... }` （无文档注释） | 无法被 `dart doc` 识别          | 添加 `/// 饲喂羊驼 [food]` |

------

###  **终极速查口诀**

> **单行 `//`，多行 `/\* \*/`，文档注释 `///` 生成链接，**
>  **`[引用]` 自动连方法，API 文档靠它出。**

------

> 💡 **总结**：
>
> - **`///` 是生成 API 文档的唯一正确方式**（普通注释 `//` 无效）
> - **`[引用]` 语法是 Dart 文档工具的核心**，必须按规范使用
>   **（所有规则基于 Dart 2.0+ 文档注释规范）**



# 4. 数据类型

## 4.1 Dart 内置类型（Built-in Types in Dart）

### 4.1.0 核心内置类型（Core Built-in Types）

Dart 语言对以下类型提供特殊支持，包括使用**字面量（literals）** 创建对象的能力。

| 类型（Type）    | 说明（Description）                      | 示例（Examples）                                        |
| --------------- | ---------------------------------------- | ------------------------------------------------------- |
| `int`           | 整数，无小数点                           | `var x = 1;`<br>`var hex = 0xDEADBEEF;`                 |
| `double`        | 64位浮点数（双精度）                     | `var y = 1.1;`<br>`var exponents = 1.42e5;`             |
| `num`           | `int` 和 `double` 的父类                 | `num x = 1;`<br>`x += 2.5; // x becomes 3.5`            |
| `String`        | 字符串（UTF-16 编码）                    | `var s1 = 'Hello';`<br>`var s2 = "World";`              |
| `bool`          | 布尔值：`true` 或 `false`                | `var isActive = true;`<br>`var isEmpty = false;`        |
| `List`          | 列表（也称数组）                         | `var list = [1, 2, 3];`<br>`var list = <int>[1, 2, 3];` |
| `Set`           | 集合（无序、唯一）                       | `var set = {1, 2, 3};`                                  |
| `Map`           | 映射（键值对）                           | `var map = {'name': 'Dart', 'age': 2};`                 |
| `Record`        | 记录（值元组）                           | `var record = ('Dart', 2.15);`                          |
| `Function`      | 函数类型                                 | `Function add = (int a, int b) => a + b;`               |
| `Runes`         | Unicode 码点（建议使用 `characters` 包） | `var runes = Runes('\u2665');`                          |
| `Symbol`        | 符号（用于标识符）                       | `#myVariable`, `#toString`                              |
| `null` (`Null`) | 空值                                     | `var value = null;`                                     |

> ✅ **提示（Tip）**: 所有变量在 Dart 中都引用对象（类的实例），因此通常可以使用构造函数初始化，如 `Map()`、`Set()` 等。



### 4.1.1 数字（Numbers）

#### 类型说明

| 类型     | 范围（平台相关）                              | 子类型       |
| -------- | --------------------------------------------- | ------------ |
| `int`    | -2⁶³ 到 2⁶³-1（原生）<br>-2⁵³ 到 2⁵³-1（Web） | `num` 的子类 |
| `double` | IEEE 754 标准的 64 位浮点数                   | `num` 的子类 |

#### 示例代码（Examples）

```dart
// 整数字面量
var x = 1;
var hex = 0xDEADBEEF;

// 浮点数字面量
var y = 1.1;
var exponents = 1.42e5; // 1.42 × 10^5

// int 自动转为 double
double z = 1; // 等价于 1.0

// 字符串与数字转换
var one = int.parse('1'); // String → int
var pi = double.parse('3.14'); // String → double
String oneStr = 1.toString(); // int → String
String piStr = 3.14159.toStringAsFixed(2); // → "3.14"
```

#### 位运算符（Bitwise Operators）——仅 `int` 支持

```dart
assert((3 << 1) == 6); // 左移：0011 → 0110
assert((3 | 4) == 7);  // 或：0011 | 0100 = 0111
assert((3 & 4) == 0);  // 与：0011 & 0100 = 0000
assert((3 ^ 4) == 7);  // 异或
```

#### 数字分隔符（Dart 3.6+）

```dart
var million = 1_000_000;
var phone = 555_123_4567;
var mac = 0x00_14_22_01_23_45;
```

> 数字分隔符是一种语法特性，允许你在整数或浮点数字面量中插入下划线 `_`，用于分组数字（例如每三位一组），**不会影响数值本身**，仅用于视觉分隔。
>
> #### 支持的数字类型
>
> - `int`（十进制、十六进制、二进制、八进制）
> - `double`（十进制和科学计数法）
>
> #### 使用规则
>
> - 下划线只能出现在数字**之间**，不能在开头、结尾或紧邻小数点/指数符号。
> - 多个下划线不能连续使用。
> - 不能替代千位分隔符以外的逻辑（如不能用于字符串）。
>
> ⚠️ 要求语言版本 ≥ 3.6。

### 4.1.2 字符串（Strings）

#### 创建方式

```dart
var s1 = '单引号';
var s2 = "双引号";
var s3 = 'It\'s easy'; // 转义
var s4 = "It's easier"; // 换引号更简单
```

#### 字符串插值（String Interpolation）

```dart
var name = "Dart";
var msg = "Hello, $name!"; // → "Hello, Dart!"
var msg2 = "Uppercase: ${name.toUpperCase()}!"; // → "DART"
```

#### 拼接与多行字符串

```dart
// 拼接
var s = 'Hello'
        ' World'; // → "Hello World"

// 多行字符串
var multi1 = '''
Line 1
Line 2
''';

var multi2 = """Also
multi-line""";

// 原始字符串（Raw String）
var raw = r'No \n newline here'; // \n 不转义
```

#### 字符串是编译时常量（Compile-time Constants）

```dart
const a = 'constant';
const b = 42;
const c = true;

const msg = '$a $b $c'; // ✅ 合法
// const invalid = '$var'; // ❌ 非 const 变量不可用
```

### 4.1.3 布尔值（Booleans）

- 只有两个值：`true` 和 `false`（均为编译时常量）
- Dart **不支持**隐式类型转换（如 `if (obj)`）

#### 正确写法（Explicit Checks）

```dart
var name = '';
assert(name.isEmpty); // 检查空字符串

var hp = 0;
assert(hp == 0); // 检查零值

var obj = null;
assert(obj == null); // 检查 null

var nan = 0 / 0;
assert(nan.isNaN); // 检查 NaN
```

------

### 4.1.4 Runes 与 Grapheme Clusters

- **Runes**: 表示字符串中的 Unicode 码点。
- **Characters 包**: 推荐用于处理用户感知的“字符”（grapheme clusters）。

#### Unicode 表示法

```dart
\u2665  // ♥ (4位十六进制)
\u{1f606} // 😆 (大括号包裹)
```

#### 使用 `characters` 包处理 emoji 等复合字符

```dart
import 'package:characters/characters.dart';

void main() {
  var hi = 'Hi 🇩🇰'; // 包含国旗 emoji
  print(hi.substring(hi.length - 1)); // ❌ 可能乱码
  print(hi.characters.last); // ✅ 正确输出 🇩🇰
}
```



### 4.1.5 Symbol(现在一般不用)

- 表示程序中声明的**标识符或操作符**。
  - 在代码压缩（minification）后仍保持唯一性，适合用于元编程或反射 API。

**Symbol** 是 Dart 中用于表示程序中**标识符（如变量名、函数名、类名）或操作符（如 `+`、`[]`）** 的不透明、唯一标识符。

- **主要用途**：在代码经过**压缩（minification）** 后，变量名可能被缩短为 `a`、`b` 等，但 `Symbol` 仍能保持其原始语义的唯一引用，因此特别适用于**反射（mirrors）** 和**元编程**。
- **语法**：使用 `#` 前缀字面量创建，例如 `#myMethod`、`#[]`。
- **不可变且唯一**：两个相同名称的 Symbol 在运行时是同一个对象（`identical(#x, #x) == true`）。
- **不包含字符串内容**：出于安全和压缩考虑，`Symbol` 不能直接转换为字符串（除非启用 `--enable-asserts` 或使用 `MirrorSystem.getName()`）。

> ⚠️ 注意：Dart 的 Web 编译（如 dart2js）默认会混淆标识符，此时只有 `Symbol` 能可靠引用原始名称。

```dart
/*#myVariable
#toString
#==*/
import 'dart:mirrors';

void main() {
  Symbol methodName = #toString;
  Symbol operator = #[];

  // 通过反射调用方法
  ClassMirror cm = reflectClass(String);
  MethodMirror method = cm.declarations[methodName] as MethodMirror;
  print(method.simpleName); // Symbol("toString")

  // 操作符示例
  print(operator); // Symbol("[]")
}
```

> ✅ Symbol 字面量是编译时常量。
>
> ##### 使用场景
>
> - 反射 API（`dart:mirrors`，仅限 VM，Web 不支持）
> - 动态调用方法名（需配合运行时信息）
> - 框架设计中作为“安全的名称引用”（避免字符串硬编码）
>
> > 📌 实际提示：由于 `dart:mirrors` 在 Flutter 和 Web 中不可用，**Symbol 在现代 Dart 开发中使用较少**，但在某些依赖反射的服务器端或测试工具中仍有价值。

### 4.1.6 其他重要类型（Other Important Types）

| 类型                | 说明                                               |
| ------------------- | -------------------------------------------------- |
| `Object`            | 所有类的根类（除 `Null`）                          |
| `Enum`              | 所有枚举类型的父类                                 |
| `Future` / `Stream` | 用于异步编程                                       |
| `Iterable`          | 用于 `for-in` 循环和生成器函数                     |
| `Never`             | 表示表达式**永远不会成功执行完成**（如总是抛异常） |
| `dynamic`           | 关闭静态类型检查（不推荐，建议用 `Object?`）       |
| `void`              | 表示**不关心返回值**，常用于函数返回类型           |

### 4.1.7 类型在继承体系中的特殊角色

- `Object`: 所有类型的超类（`Null` 除外）
- `Null`: `null` 的类型，与 `Object?` 兼容
- `Never`: 最底层类型，可赋值给任何类型
- `Object?`: `Object` 的可空版本，是 `Object` 和 `Null` 的联合类型



## 4.2 Records 记录

### 4.2.1 什么是 Records？

#### What Are Records?

**Records** 是 Dart 3.0 引入的一种 **匿名、不可变的聚合数据类型（aggregate type）**，允许开发者将多个值组合成一个单一的整体。它无需预先定义类，即可实现结构化数据的封装，类似于元组（tuple），但功能更强大。

与传统的集合类型（如 `List`、`Map`）相比，Records 具有以下关键特性：

| 对比维度         | Records 特性                                 | 其他集合类型（如 List/Map）             |
| ---------------- | -------------------------------------------- | --------------------------------------- |
| **大小**         | 固定长度（创建后字段数量不可变）             | 可变长度                                |
| **元素类型**     | 异构（不同字段可拥有不同类型）               | 通常同构（单一类型为主）                |
| **可变性**       | 不可变（创建后无法修改字段值）               | 可变                                    |
| **类型定义方式** | 结构化类型（由字段类型、名称、顺序共同决定） | 独立类型声明（需 `class` 或 `typedef`） |

```dart
// 示例：包含位置字段和命名字段的混合 Record
var record = ('first', a: 2, b: true, 'last');
```

✅ **中文说明**：
 Record 可以看作是一个“轻量级数据容器”，适用于临时打包相关数据，例如 `(用户名, 年龄, 是否登录)`，而无需专门定义一个类。

✅ **English Explanation**:
 A Record acts as a "lightweight data container" that bundles related values—e.g., `(username, age, isLoggedIn)`—without requiring a dedicated class.



### 4.2.2 核心优势

#### Core Advantages of Records

#### 1. 支持多返回值函数 ✅

##### 1. Multiple Return Values from Functions ✅

在 Dart 3.0 之前，函数只能返回单个值。若需返回多个值，通常需要借助 `Map`、`List` 或自定义 `class`，带来额外开销。现在，Records 让函数可以直接返回多个值，并支持解构赋值。

```dart
// 函数返回姓名和年龄
(String name, int age) parseUser(Map<String, dynamic> json) {
  return (json['name'] as String, json['age'] as int);
}

// 调用并解构
var (name, age) = parseUser({'name': 'Alice', 'age': 25});
print('Hello, $name! You are $age years old.');
// 输出：Hello, Alice! You are 25 years old.
```

🔹 **优势**：

- 减少样板代码（boilerplate）
- 提高可读性与类型安全性
- 避免为简单场景创建额外类

🔹 **Benefits**:

- Reduces boilerplate code
- Enhances readability and type safety
- Avoids creating classes for simple use cases

------

#### 2. 类型安全的数据结构 ✅

##### 2. Type-Safe Data Structures ✅

Records 是**结构化类型（structurally typed）**，编译器能根据字段的类型、数量和顺序进行精确的类型推断，确保类型安全。

```dart
(int, String) coordinates = (100, 'North');

var x = coordinates.$1;    // 静态类型为 int
var direction = coordinates.$2; // 静态类型为 String
```

🔹 所有字段访问都在编译时检查，避免运行时类型错误。

🔹 All field accesses are checked at compile time → safer and more predictable.

------

#### 3. 自动相等性判断 ✅

##### 3. Built-in Equality Check ✅

Records 默认实现了基于字段值的 `==` 比较逻辑。只要所有字段值相同，两个 Record 即被视为相等，即使变量名或字段标签不同。

```dart
(int x, int y) pointA = (3, 4);
(int u, int v) pointB = (3, 4);

print(pointA == pointB); // true — 字段值完全匹配
```

🔹 适用于：

- 单元测试中的断言
- 集合去重（如 `Set<Record>`）
- 缓存键值比较

🔹 Useful for:

- Assertions in unit tests
- Deduplication in sets
- Cache key comparisons

------





### 4.2.3 语法详解

#### 4.2.3 Syntax Deep Dive

##### 1. 基础语法结构

Records 支持三种字段组合方式：**仅位置字段**、**仅命名字段**、**混合字段**。

(1) 仅位置字段（Positional Fields）

```dart
(int, String) getUser() => (25, 'Lily');

var (age, name) = getUser();
print('$name is $age years old.'); // Lily is 25 years old.
```

- 使用圆括号 `(T1, T2, ...)` 定义
- 字段通过 `$1`, `$2`, ... 访问
- 顺序敏感

(2) 仅命名字段（Named Fields）

```dart
({double lat, double lng}) location = (lat: 39.9042, lng: 116.4074);

print('Latitude: ${location.lat}'); // Latitude: 39.9042
```

- 使用 `{T name}` 定义，类型可选（推荐显式声明）
- 调用时字段可乱序
- 更具可读性，适合 API 参数传递

(3) 混合字段（Mixed Fields）

```dart
var record = ('start', value: 42, active: true, 'end');

print(record.$1);        // 'start' — 第一个位置字段
print(record.value);     // 42 — 命名字段
print(record.$2);        // 'end' — 第二个位置字段
// 注意：命名字段不占用位置编号
```

> ⚠️ **重要规则**：混合 Record 的结构为 `(positional..., named...)`，命名字段必须放在末尾。

------

##### 2. 解构与模式匹配（Destructuring & Pattern Matching）

Records 天然支持解构赋值，极大提升函数式编程体验。

```dart
// 完全解构
var (x, y) = (10, 20);

// 部分解构（忽略某些字段）
var (:, y) = (100, 200); // 忽略第一个字段
print(y); // 200

// 命名字段解构
var (title: t, :year) = (title: 'Dart Guide', year: 2025);
print('$t ($year)'); // Dart Guide (2025)
```

🔹 支持在 `for-in`、`switch`、函数参数中使用模式：

```dart
void processPoint((int, int) point) {
  switch (point) {
    case (0, 0):
      print("Origin");
    case (var x, 0):
      print("On X-axis at $x");
    case (0, var y):
      print("On Y-axis at $y");
    case (var x, var y):
      print("At ($x, $y)");
  }
}
```

------

##### 3. 类型别名提升可读性（Type Aliases）

对于重复使用的 Record 结构，建议使用 `typedef` 提高代码可维护性。

```dart
typedef Coordinate = (double lat, double lng);
typedef UserInfo = ({String name, int age});

void main() {
  List<UserInfo> users = [(name: 'Alice', age: 30), (name: 'Bob', age: 28)];
  Coordinate home = (39.9042, 116.4074);
  print(home.$1);
  print(users[0].name.toUpperCase());
}
```

✅ 推荐在团队项目中为常用 Record 定义别名，增强接口清晰度。

------

### 4.2.4 典型应用场景

#### 4.2.4 Typical Use Cases

#### 1. 临时数据容器（Temporary Data Containers）

在 UI 构建中传递按钮标签和图标，无需创建额外类。

```dart
final buttons = [
  (label: "Upload", icon: Icons.upload),
  (label: "Settings", icon: Icons.settings)
];
```

####  2. 函数参数分组（Function Parameter Grouping）

将多个配置项打包传递，提升函数调用的可读性。

```dart
void showDialog(({String title, String content, bool? dismissible}) config) {
  // 处理对话框逻辑
}

// 调用示例
showDialog(
  (title: "Alert", content: "Are you sure?", dismissible: true)
);
```

#### 3. 数据处理管道（Data Processing Pipelines）

在 `map`、`where` 等链式操作中流转中间数据结构。

```dart
final result = data
  .where((item) => item.active)
  .map((item) => (item.name, item.score))
  .toList();
```

#### 4. API 返回值封装（API Return Value Wrapping）

网络请求返回状态与数据，避免使用 `Map` 或自定义 Result 类。

```dart
(Failure?, User?) login(String username, String password) async {
  try {
    final user = await api.login(username, password);
    return (null, user);
  } on Failure catch (f) {
    return (f, null);
  }
}
```

------

### 4.2.5 局限性与替代方案

#### Limitations and Alternatives

尽管 Records 功能强大，但仍存在以下限制，需谨慎评估使用场景。

| 限制项               | 说明                                      | 建议替代方案                                |
| -------------------- | ----------------------------------------- | ------------------------------------------- |
| ❌ **不可变性**       | 创建后无法修改字段值                      | 使用 `class` + `copyWith` 模式              |
| ❌ **无方法支持**     | 仅存储数据，不能定义行为（如 `toJson()`） | 升级为 `class` 或使用 **Extension Methods** |
| ❌ **类型兼容性严格** | 字段名或顺序不同即视为不同类型            | 使用统一 `typedef` 或抽象接口               |
| ❌ **性能考量**       | 高频创建可能影响性能（如循环中）          | 对大数据集使用预定义 `class`                |

------

####  何时应使用 `class` 替代 Record？

当满足以下任一条件时，建议使用 `class`：

- ✅ 需要封装行为（如 `validate()`、`toJson()`）
- ✅ 数据结构长期存在或跨模块共享
- ✅ 需要继承、多态或私有字段
- ✅ 频繁修改状态（如响应式状态管理）

##### 示例：从 Record 升级为 `class`

```dart
class UserProfile {
  final String name;
  final int age;
  final bool isActive;

  const UserProfile(this.name, this.age, this.isActive);

  Map<String, dynamic> toJson() => {
        'name': name,
        'age': age,
        'active': isActive,
      };

  UserProfile copyWith({String? name, int? age, bool? isActive}) {
    return UserProfile(
      name ?? this.name,
      age ?? this.age,
      isActive ?? this.isActive,
    );
  }
}
```

> 💡 **设计建议**：
>  使用 Record 快速原型，用 `class` 构建稳定模型。两者互补，而非替代。

------

✅ **优化说明**：

- 移除了表格中嵌套代码的问题
- 改用“小节标题 + 代码块”结构，更清晰
- 保留中英双语标题，便于国际化文档
- 所有代码均可正确渲染



------

### 4.2.6 最佳实践与性能优化

#### 4.2.6 Best Practices and Performance Tips

##### 推荐使用场景（Recommended Use Cases）

- 函数返回多个值（如解析 JSON）
- 临时中间数据（如 `map` 输出）
- 配置参数分组（避免过多参数）
- 简单数据映射（如键值对增强版）

##### 避免使用场景（Avoid When）

- 需要频繁更新字段（Records 是 immutable）
- 包含复杂业务逻辑
- 作为模型层核心数据结构（长期维护）
- 跨版本 API 返回值（结构变化易导致兼容问题）

##### 性能优化建议（Performance Tips）

| 技巧                      | 说明                                                  |
| ------------------------- | ----------------------------------------------------- |
| 🔹 避免在循环中频繁创建    | 在 `for` 循环内大量创建 Record 可能影响性能           |
| 🔹 大数据集使用类          | 如处理上千条记录，优先使用 `class` 提升效率           |
| 🔹 使用 `typedef` 统一类型 | 减少重复书写，提升可维护性                            |
| 🔹 合理选择字段类型        | 优先使用命名字段提升 API 可读性，位置字段用于简单场景 |

------

## 总结回顾（Summary）

| 章节      | 主要内容                                           |
| --------- | -------------------------------------------------- |
| **4.2.1** | Records 是匿名、不可变、结构化类型的聚合数据容器   |
| **4.2.2** | 支持多返回值、类型安全、自动相等比较               |
| **4.2.3** | 支持位置/命名/混合字段，支持解构与模式匹配         |
| **4.2.4** | 适用于临时数据、函数传参、数据流水线等场景         |
| **4.2.5** | 有不可变、无方法、类型严格等限制，必要时应升级为类 |
| **4.2.6** | 推荐用于轻量级场景，避免滥用，注意性能与可维护性   |

> 💬 **最终建议**：
>  将 Records 视为 Dart 开发中的“瑞士军刀”——小巧、灵活、高效，但不替代主工具（类）。合理使用，可显著提升代码简洁性与开发效率。

> 💬 **Final Recommendation**:
>  Treat Records as the "Swiss Army knife" of Dart—compact, flexible, and efficient—but not a replacement for full classes. Use them wisely to enhance code clarity and productivity.

------

如果你正在编写 **Flutter 应用、Dart CLI 工具或服务端 API**，现在就可以在以下位置尝试引入 Records：

- `Future<(bool, String)> login()` 返回结果
- `map((item) => (item.id, item.name))` 数据转换
- `({String label, IconData icon}) config` 参数传递