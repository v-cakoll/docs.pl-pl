---
title: ICorDebugHeapSegmentEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138446"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum — Interfejs
Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty. Ten interfejs jest podklasą interfejsu ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o regionach zarządzanej sterty.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugHeapSegmentEnum` implementuje interfejs ICorDebugEnum.  
  
 Wystąpienie `ICorDebugHeapSegmentEnum` jest wypełniane wystąpieniami [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateHeapRegions —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) . Obiekty [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapSegmentEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) .  
  
 Obiekt kolekcji `ICorDebugHeapSegmentEnum` wylicza wszystkie obszary pamięci, które mogą zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach. Może zawierać informacje dotyczące pustych lub zarezerwowanych regionów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
