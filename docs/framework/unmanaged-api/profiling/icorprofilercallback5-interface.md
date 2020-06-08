---
title: ICorProfilerCallback5 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499210"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 — Interfejs
Uzupełnia informacje ułatwiające profilerowi zidentyfikowanie pełnego zamknięcia obiektów na żywo, gdy jest używana z [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) lub [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) oraz metodami [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md) i [ConditionalWeakTableElementReferences —](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .  
  
 `ICorProfilerCallback5`musi być zaimplementowany przez profiler pamięci zarządzanej, aby subskrybować powiadomienia związane z dojściami zależnymi.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences, metoda](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Identyfikuje przechodnie zamknięcie obiektów, do których odwołują się te elementy główne za pośrednictwem bezpośrednich odwołań do pól składowych i za pośrednictwem `ConditionalWeakTable` zależności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback2 — Interfejs](icorprofilercallback2-interface.md)
