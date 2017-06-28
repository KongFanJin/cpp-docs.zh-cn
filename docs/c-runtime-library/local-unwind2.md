---
title: "_local_unwind2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_local_unwind2"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_local_unwind2"
  - "local_unwind2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_local_unwind2 函数"
  - "local_unwind2 函数"
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _local_unwind2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内部 CRT 函数。  运行在指示的范围表中列出的所有终止处理程序。  
  
## 语法  
  
```  
void _local_unwind2(    PEXCEPTION_REGISTRATION xr,    int stop );  
```  
  
#### 参数  
 \[in\] `xr`  
 与一个范围表相关联的注册记录。  
  
 \[in\] `stop`  
 指示应停止 `_local_unwind2` 的位置的词法级别。  
  
## 备注  
 此方法仅可由运行时环境使用。  请不要在代码中调用该方法。  
  
 当此方法执行终止处理程序时，它将从当前词汇级别开始，并按自己的方式运行到更高的词汇级别，直到它达到由 `stop` 指示的级别。  它不会在由 `stop` 指示的级别上执行终止处理程序。  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)