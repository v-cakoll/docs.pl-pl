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
ms.openlocfilehash: 412ade32daaed4802215c628ab94b535fc542b93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423348"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap — Metoda
Pobiera moduł wyliczający dla obiektów na stercie zarządzanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Wskaźnik do adresu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który moduł wyliczający dla obiektów, które znajdują się na stercie zarządzanej.  
  
## <a name="remarks"></a>Uwagi  
 Przed wywołaniem `ICorDebugProcess5::EnumerateHeap` metody powinny wywoływać [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) — metoda i sprawdź, czy wartość `areGCStructuresValid` pole zwracana [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) obiekt w celu zapewnienia wyliczalny pamięci sterty kolekcji w jego bieżącym stanie. Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca `E_FAIL` Jeśli dołączeniu zbyt wcześnie w okresie istnienia procesu przed pamięci dla sterty zarządzanej został przydzielony.  
  
 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiekt interfejsu jest standardowy moduł pochodną ICorDebugEnum — interfejs umożliwiający wyliczenie [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów. Ta metoda umożliwia wypełnienie [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu kolekcji z [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje o wszystkich obiektów. Kolekcja może również obejmować [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów, które nie są osadzone przez żaden obiekt, ale nie zostały zgromadzone przez moduł garbage collector.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
