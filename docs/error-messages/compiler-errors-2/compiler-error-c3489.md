---
title: 编译器错误 C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 3b192a14a39b7c0c9d264bda8073c54f0f395924
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685761"
---
# <a name="compiler-error-c3489"></a>编译器错误 C3489

当默认捕获模式为按值捕获时，要求使用“var”

当你指定 lambda 表达式的默认捕获模式是按值捕获时，不能按值将变量传递给该表达式的捕获子句。

### <a name="to-correct-this-error"></a>更正此错误

- 不要显式将变量传递给捕获子句，或者

- 不要将按值捕获指定为默认捕获模式，或者

- 将按引用捕获指定为默认捕获模式，或者

- 按引用将变量传递给捕获子句。 （这可能会更改 lambda 表达式的行为。）

## <a name="examples"></a>示例

下面的示例将生成 C3489。变量 `n` 按值出现在默认模式为按值捕获的 lambda 表达式的捕获子句中：

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

下面的示例演示 C3489 的四种可能解决方法：

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
