---
title: 如何：使用 C++ 互操作封送嵌入式指针
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
ms.openlocfilehash: 972d7a9c09100c35cb0bf527efbd0884c909c46d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544897"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>如何：使用 C++ 互操作封送嵌入式指针

下面的代码示例使用[托管的非托管](../preprocessor/managed-unmanaged.md)#pragma 指令来实现同一文件中的托管和非托管函数，但如果在单独的文件中定义，则这些函数将以相同的方式进行交互。 仅包含非托管函数的文件不需要用[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译。

## <a name="example"></a>示例

下面的示例演示如何从托管函数调用采用包含指针的结构的非托管函数。 托管函数创建结构的实例，并使用 new 关键字（而不是[ref new，gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)关键字）初始化嵌入指针。 因为这会在本机堆上分配内存，所以不需要固定数组以禁止垃圾回收。 但是，必须显式删除内存以避免内存泄露。

```cpp
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>另请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
