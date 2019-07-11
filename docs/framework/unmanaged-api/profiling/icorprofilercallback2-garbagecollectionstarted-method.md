---
title: ICorProfilerCallback2::GarbageCollectionStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4f639f9794002748e1019821514c546e4f4429f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746872"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted — Metoda
Powiadamia program profilujący kodu uruchomienia wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `cGenerations`  
 [in] Łączna liczba wpisów w `generationCollected` tablicy.  
  
 `generationCollected`  
 [in] Tablica wartości logicznych, które są `true` Jeśli generacji, która odnosi się do indeksu tablicy jest zebranych przez ten wyrzucania elementów bezużytecznych; w przeciwnym razie `false`.  
  
 Tablica jest indeksowana przez wartość [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) wyliczenia, co oznacza jego generacji.  
  
 `reason`  
 [in] Wartość [cor_prf_gc_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) wyliczenia, która wskazuje przyczynę wyrzucania elementów bezużytecznych zostało wywołane.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania zwrotne, które odnoszą się do tego wyrzucania elementów bezużytecznych nastąpi między `GarbageCollectionStarted` wywołania zwrotnego i odpowiedni [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego. Te wywołania zwrotne nie muszą występować na tym samym wątku.  
  
 Bezpiecznie programu Profiler sprawdzić obiektów w ich oryginalnej lokalizacji podczas `GarbageCollectionStarted` wywołania zwrotnego. Moduł zbierający elementy bezużyteczne rozpocznie poruszających się obiektów po powrocie z `GarbageCollectionStarted`. Po program profilujący został zwrócony z to wywołanie zwrotne, program profilujący należy wziąć pod uwagę wszystkie identyfikatory obiektu jest nieprawidłowy, dopóki nie odbierze `ICorProfilerCallback2::GarbageCollectionFinished` wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
