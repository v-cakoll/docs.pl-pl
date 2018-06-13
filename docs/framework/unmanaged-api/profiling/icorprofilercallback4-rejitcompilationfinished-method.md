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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf2e1be735150dfb006e2274c79c25649d0271d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455360"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a>ICorProfilerCallback4::ReJITCompilationFinished — Metoda
Powiadamia profilera przy użyciu kompilatora just in time (JIT) zakończenie ponownego kompilowania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która została ponownie skompilowana.  
  
 `rejitId`  
 [in] Tożsamość funkcja ponownie kompilowana JIT.  
  
 `hrStatus`  
 [in] Wartość, która wskazuje, czy ponownej kompilacji JIT zakończyła się powodzeniem.  
  
 `fIsSafeToBlock`  
 [in] `true` wskazująca, czy blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego.  
  
 Wartość `true` nie uszkodzić środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [ReJITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
