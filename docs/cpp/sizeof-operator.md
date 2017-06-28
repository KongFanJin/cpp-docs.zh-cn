---
title: "sizeof 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "sizeof_cpp"
  - "sizeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sizeof 运算符"
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# sizeof 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

产生与 `char` 类型的大小有关的操作数大小。  
  
> [!NOTE]
>  有关 `sizeof ...` 运算符的信息，请参阅[省略号和可变参数模板](../cpp/ellipses-and-variadic-templates.md)。  
  
## 语法  
  
```  
sizeof unary-expression sizeof  ( type-name )  
```  
  
## 备注  
 `sizeof` 运算符的结果为 `size_t` 类型，它是包含文件 STDDEF.H 中定义的整数类型。  利用此运算符，你可以避免在程序中指定依赖于计算机的数据大小。  
  
 `sizeof` 的操作数可以是下列项之一：  
  
-   类型名称。  若要将 `sizeof` 用于类型名称，则该名称必须用括号括起。  
  
-   一个表达式。  当用于表达式时，无论是否使用括号都可指定 `sizeof`。  不计算表达式。  
  
 当 `sizeof` 运算符应用到 `char` 类型的对象时，它将生成 1。  当 `sizeof` 运算符应用到数组时，它将产生该数组的字节总数，而非由数组标识符表示的指针的大小。  若要获取由数组标识符表示的指针的大小，请将其作为参数传递给使用 `sizeof` 的函数。  例如：  
  
## 示例  
  
```  
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## 示例输出  
  
```  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 当 `sizeof` 运算符应用到 `class`、`struct` 或 `union` 类型时，结果为该类型的对象中的字节数，以及添加的用于在字边界上对齐成员数据的任何填充。  结果不一定对应于通过将各个成员的存储需求相加计算出的大小。  [\/Zp](../build/reference/zp-struct-member-alignment.md) 编译器选项和 [pack](../preprocessor/pack.md) 杂注会影响成员的对齐边界。  
  
 `sizeof` 运算符永远不会产生 0，即使对于空类也是如此。  
  
 `sizeof` 运算符不能用于以下操作数：  
  
-   函数。  （但是，`sizeof` 可应用于指向函数的指针。）  
  
-   位域。  
  
-   未定义的类。  
  
-   `void` 类型。  
  
-   动态分配的数组。  
  
-   外部数组。  
  
-   不完整类型。  
  
-   带括号的不完整类型的名称。  
  
 当 `sizeof` 运算符应用于引用时，结果与 `sizeof` 应用到对象本身时的结果相同。  
  
 如果某个未确定大小的数组是结构的最后一个元素，则 `sizeof` 运算符将返回没有该数组的结构的大小。  
  
 `sizeof` 运算符通常用于通过使用以下形式的表达式计算数组中的元素数量：  
  
```  
sizeof array / sizeof array[0]  
```  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)