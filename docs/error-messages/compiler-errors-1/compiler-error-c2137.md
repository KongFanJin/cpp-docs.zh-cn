---
title: 编译器错误 C2137
ms.date: 11/04/2016
f1_keywords:
- C2137
helpviewer_keywords:
- C2137
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
ms.openlocfilehash: 2bc0ed5a47900b8d64e59d1b2c745b1e51e37db4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757470"
---
# <a name="compiler-error-c2137"></a>编译器错误 C2137

空字符常量

不允许使用空字符常量 (' ')。

下面的示例生成 C2137：

```cpp
// C2137.cpp
int main() {
   char c = '';   // C2137
   char d = ' ';   // OK
}
```
