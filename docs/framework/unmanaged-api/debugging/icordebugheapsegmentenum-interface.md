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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73036d1c12c46cbfda8031073a005bc9b376040e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756215"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum — Interfejs
Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty. Ten interfejs jest podklasą icordebugenum — interfejs.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje na temat regionów zarządzanego stosu.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugHeapSegmentEnum` Interfejsu implementuje interfejs ICorDebugEnum.  
  
 `ICorDebugHeapSegmentEnum` Wystąpień jest wypełniana przy użyciu [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, wywołując [icordebugprocess5::enumerateheapregions —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody. [Cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metody.  
  
 `ICorDebugHeapSegmentEnum` Obiekt kolekcji wylicza wszystkie regiony pamięci, które może zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach. Może zawierać informacji na temat regionów pamięci puste lub zastrzeżonych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
