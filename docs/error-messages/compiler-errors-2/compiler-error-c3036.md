---
title: 编译器错误 C3036
ms.date: 11/04/2016
f1_keywords:
- C3036
helpviewer_keywords:
- C3036
ms.assetid: 10c6993e-bc42-4a07-85c7-cdc34ac30906
ms.openlocfilehash: 6b723285ea1e2c58448ec9b461e655f25f95112d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508492"
---
# <a name="compiler-error-c3036"></a>编译器错误 C3036

“operator”：OpenMP“reduction”子句中的运算符标记无效

未正确指定 [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) 子句。

下面的示例生成 C3036：

```cpp
// C3036.cpp
// compile with: /openmp
static float a[1000], b[1000], c[1000];
void test1(int first, int last) {
   static float dp = 0.0f;
   #pragma omp for nowait reduction(.:dp)   // C3036
   // try the following line instead
   // #pragma omp for nowait reduction(+: dp)
   for (int i = first ; i <= last ; ++i)
      dp += a[i] * b[i];
}
```
