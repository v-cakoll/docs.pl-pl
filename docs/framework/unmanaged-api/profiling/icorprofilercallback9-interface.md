---
title: ICorProfilerCallback9 Interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991994"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 Interface
[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]  

 Podklasa klasy [ICorProfilerCallback8](icorprofilercallback8-interface.md) który zapewnia metodę wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, że metoda dynamiczna został pamięci zbierane i następnie zwolnione.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodUnloaded, metoda](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Powiadamia program profilujący, że metoda dynamiczna został pamięci zbierane i następnie zwolnione.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback9-interface.md)
- [Metoda ICorProfilerCallback8.DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [Metoda ICorProfilerCallback8.DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
