---
title: "IPersistPropertyBagImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: abef2ffa759cf74ee2316c7e0c9dd84f5c76b1d7
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 类
此类实现**IUnknown**和允许将其属性保存到客户端提供的属性包对象。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IPersistPropertyBagImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|检索对象的 CLSID。|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新创建的对象。 ATL 实现返回`S_OK`。|  
|[IPersistPropertyBagImpl::Load](#load)|从客户端提供的属性包加载对象的属性。|  
|[IPersistPropertyBagImpl::Save](#save)|将对象的属性保存到客户端提供的属性包。|  
  
## <a name="remarks"></a>备注  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx)接口允许对象将其属性保存到客户端提供的属性包。 类`IPersistPropertyBagImpl`提供默认实现此接口并实现**IUnknown**信息发送给转储设备在调试生成。  
  
 **IPersistPropertyBag**与结合工作[IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx)和[IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx)。 客户端必须实现这些后者的两个接口。 通过`IPropertyBag`，客户端将保存并加载该对象的各个属性。 通过**IErrorLog**，该对象和客户端可以报告遇到的任何错误。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID  
 检索对象的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="initnew"></a>IPersistPropertyBagImpl::InitNew  
 初始化新创建的对象。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="load"></a>IPersistPropertyBagImpl::Load  
 从客户端提供的属性包加载对象的属性。  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来检索此信息。  
  
 请参阅[IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="save"></a>IPersistPropertyBagImpl::Save  
 将对象的属性保存到客户端提供的属性包。  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来存储此信息。 默认情况下，此方法将保存所有属性，而不考虑的值*fSaveAllProperties*。  
  
 请参阅[IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [类概述](../../atl/atl-class-overview.md)
