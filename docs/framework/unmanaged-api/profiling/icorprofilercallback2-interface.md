---
title: ICorProfilerCallback2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: 3b0e60602d2f36552c3e0e85ec51205b4128486b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499769"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 — Interfejs
Dostarcza metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler. `ICorProfilerCallback2`Interfejs jest rozszerzeniem interfejsu [ICorProfilerCallback](icorprofilercallback-interface.md) . Oznacza to, że udostępnia nowe wywołania zwrotne wprowadzone w .NET Framework w wersji 2,0.  
  
> [!NOTE]
> Każda implementacja metody musi zwrócić wynik HRESULT mający wartość S_OK w przypadku powodzenia lub E_FAIL w przypadku niepowodzenia. Obecnie środowisko CLR ignoruje wartość HRESULT zwracaną przez poszczególne wywołania zwrotne, z wyjątkiem [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FinalizeableObjectQueued, metoda](icorprofilercallback2-finalizeableobjectqueued-method.md)|Powiadamia profiler kodu o tym, że obiekt z finalizatorem został umieszczony w kolejce finalizatora w celu wykonania jego `Finalize` metody.|  
|[GarbageCollectionFinished, metoda](icorprofilercallback2-garbagecollectionfinished-method.md)|Powiadamia program profilujący, że wyrzucanie elementów bezużytecznych zostało ukończone i wydano wszystkie wywołania zwrotne odzyskiwania pamięci.|  
|[GarbageCollectionStarted, metoda](icorprofilercallback2-garbagecollectionstarted-method.md)|Powiadamia profiler kodu o rozpoczęciu wyrzucania elementów bezużytecznych.|  
|[HandleCreated, metoda](icorprofilercallback2-handlecreated-method.md)|Powiadamia profiler kodu o utworzeniu dojścia do wyrzucania elementów bezużytecznych.|  
|[HandleDestroyed, metoda](icorprofilercallback2-handledestroyed-method.md)|Powiadamia profiler kodu, że dojście do wyrzucania elementów bezużytecznych zostało zniszczone.|  
|[RootReferences2, metoda](icorprofilercallback2-rootreferences2-method.md)|Powiadamia profiler o odwołaniach głównych po wystąpieniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem metody [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) .|  
|[SurvivingReferences, metoda](icorprofilercallback2-survivingreferences-method.md)|Powiadamia profiler o odwołaniach do obiektów, które przeżyły wyrzucanie elementów bezużytecznych.|  
|[ThreadNameChanged, metoda](icorprofilercallback2-threadnamechanged-method.md)|Powiadamia profiler kodu o zmianie nazwy wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę w `ICorProfilerCallback` interfejsie (lub `ICorProfilerCallback2` ) w celu powiadomienia profilera o wystąpieniu zdarzenia, do którego zasubskrybował Profiler. Jest to podstawowy interfejs wywołania zwrotnego, za pomocą którego środowisko CLR komunikuje się z profilerem kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. W przypadku .NET Framework 2,0 i nowszych wersji profiler musi również zaimplementować `ICorProfilerCallback2` metody. Każda implementacja metody musi zwrócić wynik HRESULT mający wartość S_OK w przypadku powodzenia lub E_FAIL w przypadku niepowodzenia. Obecnie środowisko CLR ignoruje wartość HRESULT zwracaną przez poszczególne wywołania zwrotne, z wyjątkiem [ICorProfilerCallback:: ObjectReferences —](icorprofilercallback-objectreferences-method.md).  
  
 Profiler kodu musi być zarejestrowany w rejestrze systemu Microsoft Windows, jego obiekt COM implementujący `ICorProfilerCallback` interfejsy i `ICorProfilerCallback2` . Profiler kodu subskrybuje zdarzenia, dla których chce otrzymywać powiadomienie przez wywołanie [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). Zwykle jest to wykonywane w implementacji profilera [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md). Profiler jest w stanie odebrać powiadomienie z środowiska uruchomieniowego, gdy zdarzenie ma miejsce lub właśnie wystąpiło w trakcie wykonywania procesu.  
  
> [!NOTE]
> Profiler rejestruje pojedynczy obiekt COM. Jeśli profiler jest ukierunkowany na .NET Framework wersja 1,0 lub 1,1, ten obiekt COM wymaga tylko implementacji metod `ICorProfilerCallback` . Jeśli jest to element docelowy .NET Framework wersja 2,0 lub nowsza, obiekt COM musi również zaimplementować metody `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback3, interfejs](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
