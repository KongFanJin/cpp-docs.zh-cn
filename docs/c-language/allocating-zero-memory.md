---
title: 分配零内存
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313488"
---
# <a name="allocating-zero-memory"></a>分配零内存

**ANSI 4.10.3** 请求的大小为零时，`calloc`、`malloc` 或 `realloc` 函数的行为

`calloc`、`malloc` 和 `realloc` 函数接受零作为参数。 不分配实际内存，但会返回有效的指针，并且之后可通过 realloc 修改内存块。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)
