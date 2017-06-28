---
title: "negative_binomial_distribution 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- negative_binomial_distribution
- random/std::negative_binomial_distribution
- random/std::negative_binomial_distribution::reset
- random/std::negative_binomial_distribution::k
- random/std::negative_binomial_distribution::p
- random/std::negative_binomial_distribution::param
- random/std::negative_binomial_distribution::min
- random/std::negative_binomial_distribution::max
- random/std::negative_binomial_distribution::operator()
- random/std::negative_binomial_distribution::param_type
- random/std::negative_binomial_distribution::param_type::k
- random/std::negative_binomial_distribution::param_type::p
- random/std::negative_binomial_distribution::param_type::operator==
- random/std::negative_binomial_distribution::param_type::operator!=
- random/std::negative_binomial_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- negative_binomial_distribution class
ms.assetid: 7f5f0967-7fdd-4578-99d4-88f292b4fe9c
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 28d1c6ab187e29198380ceab75cd588b9d69340d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="negativebinomialdistribution-class"></a>negative_binomial_distribution 类
生成负二项式分布。  
  
## <a name="syntax"></a>语法  
  
```
template<class IntType = int>
class negative_binomial_distribution
{
public:
    // types 
    typedef IntType result_type;
    struct param_type;   
    
    // constructor and reset functions
    explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
    explicit negative_binomial_distribution(const param_type& parm);
    void reset();
    
    // generating functions 
    template `<`class URNG>  
    result_type operator()(URNG& gen);
    template `<`class URNG>
    result_type operator()(URNG& gen, const param_type& parm);
    
    // property functions     
    result_type k() const;
    double p() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const; 
};
  
### Parameters  
*IntType*  
The integer result type, defaults to `int`. For possible types, see [\<random>](../standard-library/random.md).  
  
## Remarks  
The template class describes a distribution that produces values of a user-specified integral type, or type `int` if none is provided, distributed according to the Negative Binomial Distribution discrete probability function. The following table links to articles about individual members.  
  
||||  
|-|-|-|  
|[negative_binomial_distribution](#negative_binomial_distribution)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|  
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[param_type](#param_type)|  
  
The property members `k()` and `p()` return the currently stored distribution parameter values *k* and *p* respectively.  
  
The property member `param()` sets or returns the `param_type` stored distribution parameter package.  

The `min()` and `max()` member functions return the smallest possible result and largest possible result, respectively.  
  
The `reset()` member function discards any cached values, so that the result of the next call to `operator()` does not depend on any values obtained from the engine before the call.  
  
The `operator()` member functions return the next generated value based on the URNG engine, either from the current parameter package, or the specified parameter package.
  
For more information about distribution classes and their members, see [\<random>](../standard-library/random.md).  
  
For detailed information about the negative binomial distribution discrete probability function, see the Wolfram MathWorld article [Negative Binomial Distribution](http://go.microsoft.com/fwlink/LinkId=400516).  
  
## Example  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int k, const double p, const int& s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::negative_binomial_distribution<> distr(k, p);  
  
    std::cout << std::endl;  
    std::cout << "k == " << distr.k() << std::endl;  
    std::cout << "p == " << distr.p() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Histogram for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    int    k_dist = 1;  
    double p_dist = 0.5;  
    int    samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for k distribution (where 0 < k): ";  
    std::cin >> k_dist;  
    std::cout << "Enter a double value for p distribution (where 0.0 < p <= 1.0): ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for a sample count: ";  
    std::cin >> samples;  
  
    test(k_dist, p_dist, samples);  
}  
  
```  
  
首次运行：  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for k distribution (where 0 `<` k): 1  
Enter a double value for p distribution (where 0.0 `<`p `<`= 1.0): .5  
Enter an integer value for a sample count: 100  
 
k == 1  
p == 0.5  
Histogram for 100 samples:  
    0 :::::::::::::::::::::::::::::::::::::::::::  
    1 ::::::::::::::::::::::::::::::::  
    2 ::::::::::::  
    3 :::::::  
    4 ::::  
    5 ::  
```  
  
第二次运行：  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for k distribution (where 0 `<` k): 100  
Enter a double value for p distribution (where 0.0 `<` p <= 1.0): .667  
Enter an integer value for a sample count: 100  
 
k == 100  
p == 0.667  
Histogram for 100 samples:  
    31 ::  
    32 :  
    33 ::  
    34 :  
    35 ::  
    37 ::  
    38 :  
    39 :  
    40 ::  
    41 :::  
    42 :::  
    43 :::::  
    44 :::::  
    45 ::::  
    46 ::::::  
    47 ::::::::  
    48 :::  
    49 :::  
    50 :::::::::  
    51 :::::::  
    52 ::  
    53 :::  
    54 :::::  
    56 ::::  
    58 :  
    59 :::::  
    60 ::  
    61 :  
    62 ::  
    64 :  
    69 ::::  
```  
  
## <a name="requirements"></a>要求  
**标头：**\<random>  
  
**命名空间：** std  
  
##  <a name="negative_binomial_distribution"></a>negative_binomial_distribution::negative_binomial_distribution  
构造分布。  
  
```  
explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
explicit negative_binomial_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>参数  
*k*  
`k` 分布参数。  
  
*p*  
`p` 分布参数。  
  
*parm*  
用于构造分布的参数结构。  
  
### <a name="remarks"></a>备注  
**前提条件：**`0.0 < k` 和 `0.0 < p ≤ 1.0`  
  
第一个构造函数将构造一个对象，该对象存储的 `p` 值保留值 *p*，并且该对象存储的 `k` 值保留值 *k*。  
  
第二个构造函数将构造一个从 parm 初始化其存储的参数的对象。 通过调用 `param()` 成员函数，可获取和设置当前的现有分发参数。  
  
##  <a name="param_type"></a>  negative_binomial_distribution::param_type  
存储分布的参数。  
  
struct param_type {  
   typedef negative_binomial_distribution`<`result_type> distribution_type;  
   param_type(result_type k = 1, double p = 0.5); result_type k() const; double p() const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };  
  
### <a name="parameters"></a>参数  
*k*  
`k` 分布参数。  
  
*p*  
`p` 分布参数。  
  
*right*  
用于比较的 `param_type` 结构。  
  
### <a name="remarks"></a>备注  
**前置条件：**`0.0 < k` 和 `0.0 < p ≤ 1.0`  
  
在实例化时，可将此结构传递给分布的类构造函数、传递给 `param()` 成员函数以设置现有分布的存储参数，并传递给 `operator()` 以代替存储参数使用。  
  
## <a name="see-also"></a>另请参阅  
 [\<random>](../standard-library/random.md)
