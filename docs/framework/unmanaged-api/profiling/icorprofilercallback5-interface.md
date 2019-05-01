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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 114d97e02b0a6b80c46f971ed74a24dc3c397f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049677"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 — Interfejs
Uzupełnia informacje pomagające zidentyfikować pełne zamknięcie obiekty na żywo, gdy jest używana z oboma program profilujący [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) lub [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metoda wraz z [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) i [conditionalweaktableelementreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.  
  
 `ICorProfilerCallback5` muszą być zaimplementowane przez profiler pamięci zarządzanej do subskrybowania powiadomień uchwytów związanych z zależnych.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Identyfikuje przechodnie zamknięcia obiektów, odwołuje się katalogami, za pomocą odwołania do obu pól bezpośrednim członkiem i za pomocą `ConditionalWeakTable` zależności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
