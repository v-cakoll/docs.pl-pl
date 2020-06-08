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
ms.openlocfilehash: a3fb5c398b8ccd7caba0b005bcf03e64ecef4ba5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503253"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a>ICorProfilerCallback::RuntimeSuspendAborted — Metoda
Powiadamia profiler o przerwaniu zawieszenia środowiska uruchomieniowego w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a>Uwagi  
 Zawieszenie w czasie wykonywania może zostać przerwane, jeśli dwa wątki jednocześnie podejmują próbę wstrzymania środowiska uruchomieniowego.  
  
 Wywołanie zwrotne [ICorProfilerCallback:: RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md) lub `RuntimeSuspendAborted` wywołanie zwrotne nastąpi w pojedynczym wątku po wywołaniu wywołania zwrotnego [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) .  
  
 `RuntimeSuspendAborted`Wywołanie zwrotne jest gwarantowane w tym samym wątku co `RuntimeSuspendStarted` wywołanie zwrotne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
