---
title: 编译器警告（等级 4）C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 66e782c2fbb9c39c6a189de496cd0dcb4f1f4991
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218073"
---
# <a name="compiler-warning-level-4-c4559"></a>编译器警告（等级 4）C4559

> "*function*"：重定义;函数获取 __declspec （*修饰符*）

## <a name="remarks"></a>备注

重定义或重新声明了一个函数，并且第二个定义或声明添加了 **`__declspec`** 修饰符（*修饰符*）。 此警告为信息性。 若要修复此警告，请删除其中一个定义。

## <a name="example"></a>示例

下面的示例生成 C4559：

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
