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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175099"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8, interfejs
[Obsługiwane w .NET Framework 4.7 i nowszych wersjach]  

 Podklasa [ICorProfilerCallback7,](icorprofilercallback7-interface.md) która udostępnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera, że kompilacja JIT metody dynamicznej została uruchomiona i zakończona.
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Powiadamia profiler, że kompilacja JIT metody dynamicznej została uruchomiona.|  
|[DynamicMethodJITCompilationFinished, metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Powiadamia profiler, że kompilacja JIT metody dynamicznej została zakończona.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz też

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback9, interfejs](icorprofilercallback9-interface.md)
