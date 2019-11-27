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
ms.openlocfilehash: ed2553f2d971deefd85f731dd39f383cd096c5b0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439814"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted — Metoda
Powiadamia profiler kodu o rozpoczęciu odzyskiwania pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `cGenerations`  
 podczas Łączna liczba wpisów w tablicy `generationCollected`.  
  
 `generationCollected`  
 podczas Tablica wartości logicznych, które są `true`, jeśli generacja, która odpowiada indeksowi tablicy jest zbierana przez to wyrzucanie elementów bezużytecznych; w przeciwnym razie `false`.  
  
 Tablica jest indeksowana przez wartość wyliczenia [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) , która wskazuje generowanie.  
  
 `reason`  
 podczas Wartość wyliczenia [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) , która wskazuje przyczynę wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wywołania zwrotne, które odnoszą się do tego wyrzucania elementów bezużytecznych, następują między wywołaniem zwrotnym `GarbageCollectionStarted` i odpowiednim wywołaniem zwrotnym [ICorProfilerCallback2:: GarbageCollectionFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) Te wywołania zwrotne nie muszą występować w tym samym wątku.  
  
 Program profilujący może bezpiecznie zbadać obiekty w ich oryginalnych lokalizacjach podczas wywołania zwrotnego `GarbageCollectionStarted`. Moduł wyrzucania elementów bezużytecznych rozpocznie przesuwanie obiektów po powrocie z `GarbageCollectionStarted`. Po zwróceniu przez profiler z tego wywołania zwrotnego, profiler powinien wziąć pod uwagę wszystkie identyfikatory obiektów, które mają być nieprawidłowe do momentu odebrania wywołania zwrotnego `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
