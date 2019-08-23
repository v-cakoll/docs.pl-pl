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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d36d8ef3bfdbd6a1acf787a91003e2ff3139a4d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963965"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 — Interfejs
Dostarcza metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania profilera kodu o wystąpieniu zdarzeń subskrybowanych przez profiler. Interfejs jest rozszerzeniem interfejsu [ICorProfilerCallback.](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) `ICorProfilerCallback2` Oznacza to, że udostępnia nowe wywołania zwrotne wprowadzone w .NET Framework w wersji 2,0.  
  
> [!NOTE]
> Każda implementacja metody musi zwracać wynik HRESULT mający wartość S_OK dla sukcesu lub E_FAIL w przypadku niepowodzenia. Obecnie środowisko CLR ignoruje wartość HRESULT zwracaną przez poszczególne wywołania zwrotne, z wyjątkiem [ICorProfilerCallback:: ObjectReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FinalizeableObjectQueued, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Powiadamia profiler kodu o tym, że obiekt z finalizatorem został umieszczony w kolejce finalizatora w celu wykonania jego `Finalize` metody.|  
|[GarbageCollectionFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Powiadamia program profilujący, że wyrzucanie elementów bezużytecznych zostało ukończone i wydano wszystkie wywołania zwrotne odzyskiwania pamięci.|  
|[GarbageCollectionStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Powiadamia profiler kodu o rozpoczęciu wyrzucania elementów bezużytecznych.|  
|[HandleCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Powiadamia profiler kodu o utworzeniu dojścia do wyrzucania elementów bezużytecznych.|  
|[HandleDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Powiadamia profiler kodu, że dojście do wyrzucania elementów bezużytecznych zostało zniszczone.|  
|[RootReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Powiadamia profiler o odwołaniach głównych po wystąpieniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem metody [ICorProfilerCallback:: RootReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .|  
|[SurvivingReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Powiadamia profiler o odwołaniach do obiektów, które przeżyły wyrzucanie elementów bezużytecznych.|  
|[ThreadNameChanged, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Powiadamia profiler kodu o zmianie nazwy wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę w `ICorProfilerCallback` interfejsie (lub `ICorProfilerCallback2`) w celu powiadomienia profilera o wystąpieniu zdarzenia, do którego zasubskrybował Profiler. Jest to podstawowy interfejs wywołania zwrotnego, za pomocą którego środowisko CLR komunikuje się z profilerem kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. W przypadku .NET Framework 2,0 i nowszych wersji profiler musi również zaimplementować `ICorProfilerCallback2` metody. Każda implementacja metody musi zwracać wynik HRESULT mający wartość S_OK dla sukcesu lub E_FAIL w przypadku niepowodzenia. Obecnie środowisko CLR ignoruje wartość HRESULT zwracaną przez poszczególne wywołania zwrotne, z wyjątkiem [ICorProfilerCallback:: ObjectReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Profiler kodu musi być zarejestrowany w rejestrze systemu Microsoft Windows, jego obiekt com implementujący `ICorProfilerCallback` interfejsy i. `ICorProfilerCallback2` Profiler kodu subskrybuje zdarzenia, dla których chce otrzymywać powiadomienie przez wywołanie [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Zwykle jest to wykonywane w implementacji profilera [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler jest w stanie odebrać powiadomienie z środowiska uruchomieniowego, gdy zdarzenie ma miejsce lub właśnie wystąpiło w trakcie wykonywania procesu.  
  
> [!NOTE]
> Profiler rejestruje pojedynczy obiekt COM. Jeśli profiler jest ukierunkowany na .NET Framework wersja 1,0 lub 1,1, ten obiekt COM wymaga tylko implementacji metod `ICorProfilerCallback`. Jeśli jest to element docelowy .NET Framework wersja 2,0 lub nowsza, obiekt COM musi również zaimplementować metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
