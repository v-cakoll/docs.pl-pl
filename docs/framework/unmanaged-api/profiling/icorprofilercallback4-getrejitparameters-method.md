---
title: ICorProfilerCallback4::GetReJITParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f628bd1270b529264c14236ca7cdc03bf7afd9d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454209"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters — Metoda
Umożliwia profilującego można ustawić flagi generowania inny kod dla nowych treści metody ponownej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] Moduł, który zawiera metodę, dla którego CLR wymaga ustawienia parametrów ponownej kompilacji JIT.  
  
 `methodId`  
 [in] `MethodDef` Metody, dla którego CLR wymaga ustawienia parametrów ponownej kompilacji JIT.  
  
 `pFunctionControl`  
 [in] Wskaźnik do [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interfejs, który profilera mogą wykorzystywać do dostarczania informacji ponownej kompilacji JIT dla metody jest ponownie kompilowana.  
  
## <a name="remarks"></a>Uwagi  
 Problemy CLR `GetReJITParameters` wywołania zwrotnego, aby profilera można określić parametry ponowną kompilację danej metody. `GetReJITParameters` Wywołania zwrotnego jest wystawiony tylko raz dla każdej funkcji; parametry dostarczane przez profiler dotyczą wszystkich wystąpień tej funkcji.  
  
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
