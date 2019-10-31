---
title: ICorProfilerCallback9, interfejs
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136564"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9, interfejs
[Obsługiwane w .NET Framework 4.7.2 i nowszych wersjach]  

 Podklasa elementu [ICorProfilerCallback8](icorprofilercallback8-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadomienia profilera, że metoda dynamiczna została odtworzona, a następnie zwolniona z pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodUnloaded, metoda](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Powiadamia program profilujący, że metoda dynamiczna została odtworzona, a następnie zwolniona.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8. DynamicMethodJITCompilationStarted — Metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8. DynamicMethodJITCompilationFinished — Metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
