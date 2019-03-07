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
ms.openlocfilehash: 99eca9fc431d159dab47cd1add5f1fe126548b5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488893"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a>ICorProfilerCallback4::ReJITCompilationFinished — Metoda
Powiadamia program profilujący, że kompilator just-in-time (JIT) została zakończona, ponownej kompilacji funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, która była ponownie kompilowana.  
  
 `rejitId`  
 [in] Tożsamość funkcja ponownie skompilowana JIT.  
  
 `hrStatus`  
 [in] Wartość, która wskazuje, czy JIT — rekompilacja zakończyło się pomyślnie.  
  
 `fIsSafeToBlock`  
 [in] `true` do wskazania, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.  
  
 Wartość `true` nie negatywnie wpłynąć na środowisko uruchomieniowe, ale mogą mieć wpływ na wyniki profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
