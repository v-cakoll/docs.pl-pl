---
title: "ICorProfilerCallback4::ReJITCompilationStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ddcacf72d21ec076fe74a1c069311ef3f73a20c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted — Metoda
Powiadamia profilera, czy można ponownie skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji rozpoczęcia ponowną kompilację przy użyciu kompilatora JIT.  
  
 `rejitId`  
 [in] Identyfikator nowej wersji funkcji ponownej kompilacji.  
  
 `fIsSafeToBlock`  
 [in] `true` wskazująca, czy blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego. Wartość `true` nie uszkodzić środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość odbierania więcej niż jedną parę `ReJITCompilationStarted` i [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) wywołania metod dla każdej funkcji ze względu na sposób środowiska uruchomieniowego konstruktorów klas uchwytów. Na przykład środowiska uruchomieniowego uruchamia ponowną kompilację metoda, ale konstruktora klasy dla klasy B musi zostać uruchomione. W związku z tym środowiska uruchomieniowego rekompiluje konstruktora dla klasy B i uruchamia go. Konstruktor jest uruchomiona, powoduje wywołanie do metody A, co powoduje, że metoda A ponownie skompilowana. W tym scenariuszu pierwszy kompilację metoda jest zatrzymywane. Jednak zarówno próbuje ponownie skompilować metody są zgłaszane zdarzenia ponownej kompilacji JIT.  
  
 Profilery musi obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, gdy dwa wątków jednocześnie dokonywania wywołań zwrotnych. Na przykład wywołuje wątku A `ReJITCompilationStarted`; jednak przed wywołania wątku A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), wywołania wątku B [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) o identyfikatorze — funkcja z `ReJITCompilationStarted` wywołania zwrotnego dla wątku A. Wydaje się, że identyfikator funkcji należy jeszcze być nieprawidłowe ponieważ wywołania [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) nie ma jeszcze odebrane profilera. Jednak w takim przypadku funkcja identyfikator jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [ReJITCompilationFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
