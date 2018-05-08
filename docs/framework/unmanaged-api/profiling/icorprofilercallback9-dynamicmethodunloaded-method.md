---
title: ICorProfilerCallback9::DynamicMethodUnloaded — metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16b3334647922f845645e6eb58db3146f4c9b936
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>ICorProfilerCallback9::DynamicMethodUnloaded — metoda
[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]  
  
Powiadamia profilera zawsze, gdy dynamiczna metoda jest Odzyskiwanie zbierane i następnie zwalnianie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
#### <a name="parameters"></a>Parametry  
[in] `functionId`  
Identyfikator funkcji w pamięci, która została odzyskiwanie zbierane i zwalnianie modułu.   

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też  
[ICorProfilerCallback8.DynamicMethodJITCompilationStarted — metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
[ICorProfilerCallback8.DynamicMethodJITCompilationFinished — metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
[Interfejs ICorProfilerCallback9](icorprofilercallback9-interface.md)   
[COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
