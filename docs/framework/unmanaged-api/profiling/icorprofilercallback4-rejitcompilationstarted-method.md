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
ms.openlocfilehash: 6e340fa08800f31d36e6cfb280cac847a4fca548
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499353"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted — Metoda
Powiadamia profiler, że został uruchomiony kompilator just-in-Time (JIT), aby ponownie skompilować funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, którą rozpoczęło ponowne kompilowanie kompilatora JIT.  
  
 `rejitId`  
 podczas Identyfikator ponownej kompilacji nowej wersji funkcji.  
  
 `fIsSafeToBlock`  
 [w] `true` Aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false`, aby wskazać, że blokowanie nie wpłynie na działanie środowiska uruchomieniowego. Wartość nie jest `true` szkodliwe dla środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość otrzymywania więcej niż jednej pary `ReJITCompilationStarted` i wywołań metod [ReJITCompilationFinished —](icorprofilercallback4-rejitcompilationfinished-method.md) dla każdej funkcji ze względu na sposób, w jaki środowisko uruchomieniowe obsługuje konstruktory klas. Na przykład środowisko uruchomieniowe zaczyna ponownie kompilować metodę A, ale Konstruktor klasy dla klasy B musi być uruchomiony. W związku z tym środowisko uruchomieniowe ponownie kompiluje Konstruktor dla klasy B i uruchamia go. Gdy Konstruktor jest uruchomiony, wywołuje metodę A, która powoduje ponowne skompilowanie metody A. W tym scenariuszu pierwsza ponowna kompilacja metody A jest zatrzymywana. Jednak obie próby rekompilacji metody A są raportowane przy użyciu zdarzeń ponownej kompilacji JIT.  
  
 Profilowani muszą obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, gdy dwa wątki jednocześnie wydają wywołania zwrotne. Na przykład wywołanie Thread A, `ReJITCompilationStarted` jednak przed wywołaniem wątku [ReJITCompilationFinished —](icorprofilercallback4-rejitcompilationfinished-method.md), wątek B wywołuje [ICorProfilerCallback:: ExceptionSearchFunctionEnter —](icorprofilercallback-exceptionsearchfunctionenter-method.md) z identyfikatorem funkcji z `ReJITCompilationStarted` wywołania zwrotnego wątku A. Może się wydawać, że identyfikator funkcji nie powinien jeszcze być prawidłowy, ponieważ wywołanie [ReJITCompilationFinished —](icorprofilercallback4-rejitcompilationfinished-method.md) nie zostało jeszcze odebrane przez profiler. Jednak w tym przypadku identyfikator funkcji jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
- [JITCompilationFinished, metoda](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished, metoda](icorprofilercallback4-rejitcompilationfinished-method.md)
