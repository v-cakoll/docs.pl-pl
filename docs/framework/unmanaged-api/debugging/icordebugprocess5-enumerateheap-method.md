---
title: ICorDebugProcess5::EnumerateHeap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b404b7762e085eb44f0bd3b448fcee9eab9a3c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103912"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap — Metoda
Pobiera moduł wyliczający dla obiektów na stosie zarządzanym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Wskaźnik na adres [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który jest moduł wyliczający dla obiektów, które znajdują się na zarządzanym stosie.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem `ICorDebugProcess5::EnumerateHeap` metody powinny wywoływać [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody i sprawdzić wartość `areGCStructuresValid` pole zwracanego [cor_heapinfo —](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) obiekt do upewnij się, że stercie wyrzucania elementów bezużytecznych w jego bieżącym stanie wyliczalny. Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca `E_FAIL` Jeśli dołączysz zbyt wcześnie w trakcie trwania procesu przed pamięci dla zarządzanego stosu jest przydzielony.  
  
 [Icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu jest standardowy moduł wyliczający, pochodzące z icordebugenum — interfejs umożliwiający wyliczenie [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów. Ta metoda wypełni [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu kolekcji z [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które udostępniają informacje o wszystkich obiektach. Kolekcja może również obejmować [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje o obiektach, które nie są zakorzenione przez żaden obiektu, ale nie został zebrany przez moduł odśmiecania pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5 — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
