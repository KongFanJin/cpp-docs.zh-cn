---
title: ostream_iterator 类
ms.date: 11/04/2016
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
ms.openlocfilehash: 97367c19d0b1bdb4b9c16d5d12621210c8562485
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224664"
---
# <a name="ostream_iterator-class"></a>ostream_iterator 类

类模板 ostream_iterator 描述一个输出迭代器对象，该对象使用提取内容将连续的元素写入输出流 `operator <<` 。

## <a name="syntax"></a>语法

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>参数

*类别*\
要插入到输出流的对象的类型。

*CharType*\
表示 `ostream_iterator` 字符类型的类型。 此参数是可选的，默认值为 **`char`** 。

*特征*\
表示 `ostream_iterator` 字符类型的类型。 此参数是可选的，默认值为 `char_traits` \< *CharType> . *

ostream_iterator 类必须满足对输出迭代器的需求。 可使用 `ostream_iterator` 直接向输出流中写入算法。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[ostream_iterator](#ostream_iterator)|构造已初始化并限定写入输出流的 `ostream_iterator`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|为 `ostream_iterator` 的字符类型提供的类型。|
|[ostream_type](#ostream_type)|为 `ostream_iterator` 的流类型提供的类型。|
|[traits_type](#traits_type)|为 `ostream_iterator` 的字符特征类型提供的类型。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[操作员](#op_star)|用于实现输出迭代器表达式的取消引用运算符 \* `i`  =  `x` 。|
|[operator + +](#op_add_add)|一种非功能性递增运算符，可向调用该运算之前所处理的同一对象返回 `ostream_iterator`。|
|[operator =](#op_eq)|用于实现输出迭代器表达式的赋值运算符， \* `i`  =  `x` 用于写入输出流。|

## <a name="requirements"></a>要求

**标头：**\<iterator>

**命名空间:** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a>ostream_iterator：： char_type

为迭代器的字符类型提供的类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `CharType` 的同义词。

### <a name="example"></a>示例

```cpp
// ostream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to the output stream\n"
        << "by intOut are:" << endl;
*intOut = 10;
*intOut = 20;
*intOut = 30;
}
/* Output:
The integers written to the output stream
by intOut are:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a>ostream_iterator：： operator *

用于实现输出迭代器表达式 \* *ii*  =  *x*的取消引用运算符。

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>返回值

对 `ostream_iterator` 的引用。

### <a name="remarks"></a>备注

必须满足的输出迭代器的要求 `ostream_iterator` 仅要求表达式 \* *ii*  =  *t*为有效，而不是 **`operator`** 自己的或 `operator=` 本身。 此实现中的成员运算符返回** \* this**。

### <a name="example"></a>示例

```cpp
// ostream_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a>ostream_iterator：： operator + +

一种非功能性递增运算符，可向调用该运算之前所处理的同一对象返回 `ostream_iterator`。

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>返回值

对 `ostream_iterator` 的引用。

### <a name="remarks"></a>备注

这些成员运算符都返回** \* this**。

### <a name="example"></a>示例

```cpp
// ostream_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a>ostream_iterator：： operator =

赋值运算符，用于实现用于 \* `i`  =  `x` 写入到输出流的 output_iterator 表达式。

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>参数

*初始值*\
要插入到输出流的 `Type` 类型的对象的值。

### <a name="return-value"></a>返回值

运算符将*val*插入与对象关联的输出流，后跟[ostream_iterator 构造函数](#ostream_iterator)（如果有）中指定的分隔符，然后返回对的引用 `ostream_iterator` 。

### <a name="remarks"></a>备注

必须满足的输出迭代器的要求 `ostream_iterator` 仅要求表达式 \* `ii`  =  `t` 有效，且不会对运算符或运算符 = 自行显示任何内容。 此成员运算符返回 **`*this`** 。

### <a name="example"></a>示例

```cpp
// ostream_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a>ostream_iterator：： ostream_iterator

构造已初始化并限定写入输出流的 `ostream_iterator`。

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>参数

*_Ostr*\
将遍历的 [ostream_iterator::ostream_type](#ostream_type) 类型的输出流。

*_Delimiter*\
用于插入到值之间的输出流中的分隔符。

### <a name="remarks"></a>备注

第一个构造函数通过 `&_Ostr` 初始化输出流指针。 分隔符字符串指针将指定一个空字符串。

第二个构造函数通过初始化输出流指针 `&_Ostr` ，并将分隔符字符串指针与 *_Delimiter*。

### <a name="example"></a>示例

```cpp
// ostream_iterator_ostream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   ostream_iterator<int> intOut ( cout , "\n" );
*intOut = 10;
   intOut++;
*intOut = 20;
   intOut++;

   int i;
   vector<int> vec;
   for ( i = 1 ; i < 7 ; ++i )
   {
      vec.push_back (  i );
   }

   // Write elements to standard output stream
   cout << "Elements output without delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout ) );
   cout << endl;

   // Write elements with delimiter " : " to output stream
   cout << "Elements output with delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout, " : " ) );
   cout << endl;
}
/* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*/
```

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a>ostream_iterator：： ostream_type

为迭代器的流类型提供的类型。

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>备注

该类型是[basic_ostream](../standard-library/basic-ostream-class.md) <  `CharType` `Traits` iostream 层次结构的一个 stream 类的> basic_ostream 同义词，它定义可用于写入的对象。

### <a name="example"></a>示例

有关如何声明和使用 `ostream_type` 的示例，请参阅 [ostream_iterator](#ostream_iterator)。

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a>ostream_iterator：： traits_type

为迭代器的字符特征类型提供的类型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `Traits` 的同义词。

### <a name="example"></a>示例

```cpp
// ostream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // The following not OK, but are just the default values:
   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to output stream\n"
        << "by intOut are:" << endl;
*intOut = 1;
*intOut = 10;
*intOut = 100;
}
/* Output:
The integers written to output stream
by intOut are:
1
10
100
*/
```

## <a name="see-also"></a>另请参阅

[\<iterator>](../standard-library/iterator.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 标准库参考](../standard-library/cpp-standard-library-reference.md)
