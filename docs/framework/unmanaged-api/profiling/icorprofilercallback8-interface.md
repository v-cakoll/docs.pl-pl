---
title: Interfejs ICorProfilerCallback8
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8-interface"></a>Interfejs ICorProfilerCallback8
[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]  

 Podklasa [ICorProfilerCallback7](icorprofilercallback7-interface.md) zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomiono profiler kompilacji JIT metody dynamicznej ma rozpoczęcia i zakończenia. 
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted — metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Powiadamia profilera uruchomienia kompilacji JIT metody dynamicznej.|  
|[DynamicMethodJITCompilationFinished — metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Powiadamia profilera zakończenie kompilacji JIT metody dynamicznej.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też  
[Interfejsy profilowania](profiling-interfaces.md)   
[Interfejs ICorProfilerCallback9](icorprofilercallback9-interface.md)
