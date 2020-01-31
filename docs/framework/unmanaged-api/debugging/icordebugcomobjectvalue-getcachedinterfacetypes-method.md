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
ms.openlocfilehash: f720b06581ac60c8bd68dc5e85f15843fd9425f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788906"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda
Dostarcza moduł wyliczający dla typów interfejsów, do których rzutuje bieżący obiekt lub którego używał.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIInspectableOnly`  
 podczas Wartość wskazująca, czy metoda zwraca tylko interfejsy środowisko wykonawcze systemu Windows (interfejsy`IInspectable`) lub wszystkie interfejsy COM buforowane przez otokę, która umożliwia wywoływanie (OTOKa) środowiska uruchomieniowego.  
  
 `ppInterfacesEnum`  
 określoną Wskaźnik do adresu modułu wyliczającego ICorDebugTypeEnum, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują buforowane typy interfejsów filtrowane według `bIInspectableOnly`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugComObjectValue, interfejs](icordebugcomobjectvalue-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
