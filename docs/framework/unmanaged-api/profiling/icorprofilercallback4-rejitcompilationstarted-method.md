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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a65de26f3fc088b292ec9f8a96ca4e503a17edd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680907"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted — Metoda
Powiadamia program profilujący, że kompilator just-in-time (JIT) została uruchomiona ponownie skompilować funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która została uruchomiona ponownie skompilować kompilator JIT.  
  
 `rejitId`  
 [in] Identyfikator kompilacji nową wersję funkcji.  
  
 `fIsSafeToBlock`  
 [in] `true` do wskazania, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego. Wartość `true` nie negatywnie wpłynąć na środowisko uruchomieniowe, ale mogą mieć wpływ na wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Jest to możliwe, aby otrzymać więcej niż jedną parę `ReJITCompilationStarted` i [rejitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metoda wywołuje dla każdej funkcji ze względu na sposób środowisko wykonawcze obsługuje Konstruktory klasy. Na przykład środowisko uruchomieniowe uruchamia ponownie skompilować metody A, ale konstruktora klasy dla klasy B musi zostać uruchomione. W związku z tym środowisko uruchomieniowe następuje rekompilacja konstruktora dla klasy B i uruchamia go. Po uruchomieniu Konstruktora tworzy wywołanie metody A, co powoduje, że metoda A ponownie skompilowana. W tym scenariuszu kompilację pierwszej metody A jest zatrzymywana. Jednak zarówno próbuje ponownie skompilować metody, które są zgłaszane wraz z zdarzenia ponownej kompilacji JIT.  
  
 Profilery muszą obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, w której dwa wątki jednocześnie wykorzystują wywołania zwrotne. Na przykład, wątek A wywołuje `ReJITCompilationStarted`; jednak przed wywołań wątku A [rejitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), wywołań wątku B [icorprofilercallback::exceptionsearchfunctionenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) o identyfikatorze — funkcja z `ReJITCompilationStarted` wywołania zwrotnego dla wątku A. Wydaje się, że identyfikator funkcji nie powinny jeszcze być prawidłowy ponieważ wywołanie [rejitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) nie ma jeszcze odebrane przez profiler. Jednak w tym przypadku identyfikator funkcji jest nieprawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
