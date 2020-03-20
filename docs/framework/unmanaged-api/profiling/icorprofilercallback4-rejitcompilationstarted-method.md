---
title: ICorProfilerCallback4::ReJITCompilationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177081"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted — Metoda
Powiadamia profiler, że kompilator just-in-time (JIT) rozpoczął ponowne kompilowanie funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [w] Identyfikator funkcji, którą kompilator JIT zaczął ponownie kompilować.  
  
 `rejitId`  
 [w] Identyfikator ponownej kompilacji nowej wersji funkcji.  
  
 `fIsSafeToBlock`  
 [w] `true` aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe czekać na wątek wywołujący do powrotu z tego wywołania zwrotnego; `false` , aby wskazać, że blokowanie nie wpłynie na działanie środowiska wykonawczego. Wartość `true` nie szkodzi środowiska wykonawczego, ale może mieć wpływ na wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość odbierania więcej niż `ReJITCompilationStarted` jedną parę i [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) metoda wywołuje dla każdej funkcji ze względu na sposób, w jaki środowisko uruchomieniowe obsługuje konstruktorów klas. Na przykład środowisko wykonawcze rozpoczyna ponowne kompilowanie metody A, ale konstruktor klasy dla klasy B musi zostać uruchomiony. W związku z tym środowisko wykonawcze ponownie kompiluje konstruktora dla klasy B i uruchamia go. Gdy konstruktor jest uruchomiony, wywołuje metodę A, co powoduje, że metoda A ma zostać ponownie skompilowana. W tym scenariuszu pierwsza ponowna kompilacja metody A jest zatrzymana. Jednak obie próby ponownej kompilacji metody A są zgłaszane ze zdarzeniami ponownej kompilacji JIT.  
  
 Profilerzy muszą obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, gdy dwa wątki są jednocześnie wykonywanie wywołań zwrotnych. Na przykład wątek A wywołuje `ReJITCompilationStarted`; jednak przed wątkiem A wywołuje [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), wątek B wywołuje [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) z funkcją ID z wywołania zwrotnego `ReJITCompilationStarted` dla wątku A. Może się wydawać, że identyfikator funkcji nie powinien być jeszcze prawidłowy, ponieważ wywołanie [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) nie zostało jeszcze odebrane przez profiler. Jednak w tym przypadku identyfikator funkcji jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
- [JITCompilationFinished, metoda](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished, metoda](icorprofilercallback4-rejitcompilationfinished-method.md)
