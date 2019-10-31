---
title: ICorProfilerCallback8, interfejs
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136450"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8, interfejs
[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]  

 Podklasa elementu [ICorProfilerCallback7](icorprofilercallback7-interface.md) , która zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o rozpoczęciu i zakończeniu kompilacji JIT metody dynamicznej. 
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Powiadamia profiler, że została rozpoczęta kompilacja JIT metody dynamicznej.|  
|[DynamicMethodJITCompilationFinished, metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Powiadamia profiler, że zakończyła się kompilacja JIT metody dynamicznej.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback9, interfejs](icorprofilercallback9-interface.md)
