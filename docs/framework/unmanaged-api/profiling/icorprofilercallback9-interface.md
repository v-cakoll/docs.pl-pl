---
title: Interfejs ICorProfilerCallback9
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
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452380"
---
# <a name="icorprofilercallback9-interface"></a>Interfejs ICorProfilerCallback9
[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]  

 Podklasa [ICorProfilerCallback8](icorprofilercallback8-interface.md) zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomiono profilera, czy dynamiczna metoda został odzyskiwanie zbierane i następnie zwalnianie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodUnloaded — metoda](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Powiadamia profilera, czy dynamiczna metoda został odzyskiwanie zbierane i następnie zwalnianie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Zobacz też  
[Interfejsy profilowania](profiling-interfaces.md)   
[Interfejs ICorProfilerCallback8](icorprofilercallback9-interface.md)   
[ICorProfilerCallback8.DynamicMethodJITCompilationStarted — metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)   
[ICorProfilerCallback8.DynamicMethodJITCompilationFinished — metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
