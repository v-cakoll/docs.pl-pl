---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a74b3c90c11f799f5b9738e84d33b603f0ef04
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485476"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda
Dostarcza moduł wyliczający dla typów interfejsu, czy bieżący obiekt został rzutować lub używany jako.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIInspectableOnly`  
 [in] Wartość, która wskazuje, czy metoda ta zwraca tylko [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfejsów (`IInspectable` interfejsów) lub wszystkie interfejsy COM, buforowane przez otoka wywoływana w czasie wykonywania (RCW).  
  
 `ppInterfacesEnum`  
 [out] Wskaźnik na adres icordebugtypeenum — moduł wyliczający, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują typy interfejsu w pamięci podręcznej filtrowane zgodnie z opisem w `bIInspectableOnly`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugComObjectValue, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
