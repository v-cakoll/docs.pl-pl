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
ms.openlocfilehash: c6a218b58ed2ab40505204768f7d6071dea6db5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 — Interfejs
Udostępnia metody, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania profilera kodu występowania zdarzeń, do których subskrybowanych profilera. `ICorProfilerCallback2` Interfejsu jest rozszerzeniem [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interfejsu. Oznacza to, że zapewnia nowy wywołania zwrotne wprowadzone w programie .NET Framework w wersji 2.0.  
  
> [!NOTE]
>  Każda implementacja metody musi zwracać HRESULT posiadające wartość S_OK na powodzenie lub E_FAIL w przypadku awarii. Obecnie CLR ignoruje HRESULT, zwracane przez każdego wywołania zwrotnego z wyjątkiem [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FinalizeableObjectQueued, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Powiadamia profilera kodu, że obiekt o finalizator zostało umieszczone w kolejce do wątku finalizatora dla wykonywania jego `Finalize` metody.|  
|[GarbageCollectionFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Powiadamia profilera wyrzucania elementów bezużytecznych zostało ukończone, a wszystkie wywołania zwrotne kolekcji pamięci zostały wydane dla niego.|  
|[GarbageCollectionStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Powiadamia profilera kodu rozpoczęto wyrzucania elementów bezużytecznych.|  
|[HandleCreated, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Powiadamia profilera kodu utworzono uchwyt kolekcji pamięci.|  
|[HandleDestroyed, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Powiadamia profilera kodu zniszczono dojścia kolekcji pamięci.|  
|[RootReferences2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Powiadamia profilera odwołania głównego informacje po zakończeniu wyrzucania elementów bezużytecznych. Ta metoda jest rozszerzeniem [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.|  
|[SurvivingReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Powiadamia profilera o odwołania do obiektów, które mają udało przetrwać wyrzucania elementów bezużytecznych.|  
|[ThreadNameChanged, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Powiadamia profilera kodu zmienił nazwę wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metodę `ICorProfilerCallback` (lub `ICorProfilerCallback2`) interfejsu powiadomiono profilera, gdy zdarzenie, do którego ma subskrypcję profilera, występuje. Jest interfejsem podstawowym wywołania zwrotnego, za pomocą którego CLR komunikuje się z profilera kodu.  
  
 Profiler kodu musi implementować metody `ICorProfilerCallback` interfejsu. .NET Framework 2.0 i nowszych, profilera musi implementować też `ICorProfilerCallback2` metody. Każda implementacja metody musi zwracać HRESULT posiadające wartość S_OK na powodzenie lub E_FAIL w przypadku awarii. Obecnie CLR ignoruje HRESULT, zwracane przez każdego wywołania zwrotnego z wyjątkiem [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Profiler kodu, zarejestruj się w rejestrze systemu Windows, jego obiektu COM, który implementuje `ICorProfilerCallback` i `ICorProfilerCallback2` interfejsów. Profiler kodu subskrybuje zdarzenia, dla których chce otrzymywać powiadomienia przez wywołanie metody [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Zwykle odbywa się w celu wykonania profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler może następnie otrzymywanie powiadomień z środowiska uruchomieniowego zdarzenie może nastąpić lub po prostu wystąpił podczas wykonywania procesu obsługi.  
  
> [!NOTE]
>  Profiler rejestruje pojedynczego obiektu COM. Jeśli profiler jest przeznaczona dla .NET Framework w wersji 1.0 lub 1.1, obiektu modelu COM musi zawierać implementację tylko metody `ICorProfilerCallback`. Jeśli jest docelowo .NET Framework w wersji 2.0 i później, obiektu modelu COM musi także implementować metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
