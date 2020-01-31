---
title: ICorProfilerCallback::RuntimeThreadSuspended — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: c8645bf828d0ad99bd25c1909cbee3314a11abf9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865873"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended — Metoda
Powiadamia profiler o wstrzymaniu określonego wątku lub o zawieszeniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 podczas Identyfikator wątku, który został zawieszony.  
  
## <a name="remarks"></a>Uwagi  
 Powiadomienie `RuntimeThreadSuspended` może wystąpić w dowolnym momencie między [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) i skojarzonymi [ICorProfilerCallback:: RuntimeResumeStarted —](icorprofilercallback-runtimeresumestarted-method.md) wywołaniami zwrotnymi. Powiadomienia występujące między [ICorProfilerCallback:: RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` są przeznaczone dla wątków, które były uruchomione w kodzie niezarządzanym i zostały zawieszone po wprowadzeniu do środowiska uruchomieniowego.  
  
 Ogólnie rzecz biorąc to wywołanie zwrotne występuje zaraz po wstrzymaniu wątku. Jeśli jednak aktualnie wykonywany wątek (wątek, który wywołuje to wywołanie zwrotne) jest zawieszeniem, to wywołanie zwrotne zostanie wykonane tuż przed wstrzymaniem wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [RuntimeThreadResumed, metoda](icorprofilercallback-runtimethreadresumed-method.md)
