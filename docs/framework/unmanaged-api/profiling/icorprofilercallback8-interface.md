---
title: ICorProfilerCallback8 Interface
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
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049729"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 Interface
[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]  

 Podklasa klasy [ICorProfilerCallback7](icorprofilercallback7-interface.md) zapewniający metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, który kompilację JIT metoda dynamiczna ma rozpoczęcia i zakończenia. 
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Powiadamia program profilujący rozpoczęto kompilację JIT metodę dynamiczną.|  
|[DynamicMethodJITCompilationFinished, metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Powiadamia program profilujący zakończenie kompilację JIT metodę dynamiczną.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerCallback9, interfejs](icorprofilercallback9-interface.md)
