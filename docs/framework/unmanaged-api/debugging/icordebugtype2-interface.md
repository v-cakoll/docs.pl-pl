---
title: ICorDebugType2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 878941f7af71fa5e3de8e38c4a68a66cb964983d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223163"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2, interfejs
Rozszerza interfejs ICorDebugType, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).  
  
## <a name="methods"></a>Metody  
  
|Metoda||  
|------------|-|  
|[GetTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Pobiera [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest logicznym rozszerzeniem icordebugtype — interfejs.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu ilustruje użycie [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody.  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
