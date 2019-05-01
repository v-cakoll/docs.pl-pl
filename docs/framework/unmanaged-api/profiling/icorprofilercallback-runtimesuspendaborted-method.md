---
title: ICorProfilerCallback::RuntimeSuspendAborted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9aaf7325b8e7e65aa98904513cc7efe94e35087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041811"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a>ICorProfilerCallback::RuntimeSuspendAborted — Metoda
Powiadamia program profilujący, że środowisko uruchomieniowe przerwała zawieszenie środowiska uruchomieniowego, który został pojawiają się.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a>Uwagi  
 Zawieszenie środowiska wykonawczego mogą zostało przerwane, jeśli dwa wątki jednocześnie podejmie próbę wstrzymania w czasie wykonywania.  
  
 Albo [icorprofilercallback::runtimesuspendfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) wywołanie zwrotne lub `RuntimeSuspendAborted` nastąpi wywołanie zwrotne po jednym wątkiem [icorprofilercallback::runtimesuspendstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) Wywołanie zwrotne.  
  
 `RuntimeSuspendAborted` Wywołania zwrotnego jest gwarantowane, odbywa się na tym samym wątku jako `RuntimeSuspendStarted` wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
