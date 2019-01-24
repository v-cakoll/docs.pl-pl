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
ms.openlocfilehash: 513fb623e328a8fa3abb1531715026ff9b6bf97e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558088"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 — Interfejs
Udostępnia metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR), aby powiadomić profiler kodu po wystąpieniu zdarzenia, dla których zostały zasubskrybowane przez profiler. `ICorProfilerCallback2` Interfejs jest rozszerzeniem [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu. Oznacza to udostępnia nowe wywołania zwrotne wprowadzone w programie .NET Framework w wersji 2.0.  
  
> [!NOTE]
>  Każda implementacja metody musi zwracać wartość HRESULT mających wartość S_OK od tego, czy E_FAIL w przypadku niepowodzenia. Obecnie CLR ignoruje HRESULT, który jest zwracany przez każdego wywołania zwrotnego z wyjątkiem [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FinalizeableObjectQueued, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Powiadamia program profilujący kodu, że obiekt z finalizatorem została umieszczona w kolejce do wątku finalizatora do wykonywania swoich `Finalize` metody.|  
|[GarbageCollectionFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Powiadamia program profilujący, że wyrzucania elementów bezużytecznych zostało ukończone, a wszystkie wywołania wyrzucania elementów bezużytecznych zostały wydane dla niego.|  
|[GarbageCollectionStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Powiadamia program profilujący kodu uruchomienia wyrzucania elementów bezużytecznych.|  
|[HandleCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Powiadamia program profilujący kodu utworzono uchwyt kolekcji wyrzucania elementów.|  
|[HandleDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Powiadamia program profilujący kodu zniszczono uchwyt kolekcji wyrzucania elementów.|  
|[RootReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Powiadamia program profilujący o odwołaniach do katalogu głównego, po przeprowadzeniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.|  
|[SurvivingReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Powiadamia program profilujący o odwołania do obiektów, które przetrwały wyrzucanie elementów bezużytecznych.|  
|[ThreadNameChanged, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Powiadamia program profilujący kodu, że zmieniono nazwę wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę `ICorProfilerCallback` (lub `ICorProfilerCallback2`) występuje w interfejsie powiadomić profiler, gdy zdarzenie, do którego program profilujący ma subskrypcję,. Jest to interfejs podstawowy wywołania zwrotnego, za pomocą którego CLR komunikuje się za pomocą programu profilującego kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. .NET Framework 2.0 i nowszych, program profilujący musi implementować też `ICorProfilerCallback2` metody. Każda implementacja metody musi zwracać wartość HRESULT mających wartość S_OK od tego, czy E_FAIL w przypadku niepowodzenia. Obecnie CLR ignoruje HRESULT, który jest zwracany przez każdego wywołania zwrotnego z wyjątkiem [icorprofilercallback::objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Profiler kodu należy zarejestrować w rejestrze systemu Microsoft Windows, jego obiekt COM, który implementuje `ICorProfilerCallback` i `ICorProfilerCallback2` interfejsów. Profiler kodu subskrybuje do zdarzeń, dla których chce otrzymywać powiadomienia, wywołując [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Zazwyczaj jest to realizowane w implementacji programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Program profilujący jest możliwość odbierania powiadomień ze środowiska wykonawczego, gdy zdarzenie może nastąpić lub tylko podczas wykonywania procesu środowiska uruchomieniowego.  
  
> [!NOTE]
>  Program profilujący rejestruje pojedynczy obiekt COM. Jeśli program profilujący jest przeznaczony dla .NET Framework w wersji 1.0 i 1.1, ten obiekt COM musi zawierać implementację tylko metody `ICorProfilerCallback`. Jeśli jest przeznaczony dla .NET Framework w wersji 2.0 i nowszych obiektu COM musi implementować też metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
