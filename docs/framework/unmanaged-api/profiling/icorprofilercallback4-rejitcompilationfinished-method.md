---
title: ICorProfilerCallback4::ReJITCompilationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: 9a42198b1c89dbc47c6659564cf32738b683697b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439305"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a>ICorProfilerCallback4::ReJITCompilationFinished — Metoda
Powiadamia profiler, że kompilator just-in-Time (JIT) zakończył ponowną kompilację funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, która została ponownie skompilowana.  
  
 `rejitId`  
 podczas Tożsamość funkcji ponownie skompilowanej JIT.  
  
 `hrStatus`  
 podczas Wartość wskazująca, czy ponowna kompilacja JIT zakończyła się pomyślnie.  
  
 `fIsSafeToBlock`  
 [in] `true` wskazujący, że blokowanie może spowodować, że środowisko uruchomieniowe poczeka na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false` wskazujący, że blokowanie nie ma wpływu na działanie środowiska uruchomieniowego.  
  
 Wartość `true` nie jest szkodliwe dla środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
