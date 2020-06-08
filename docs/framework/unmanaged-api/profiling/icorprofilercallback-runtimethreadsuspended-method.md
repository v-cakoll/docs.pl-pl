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
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503201"
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
 `RuntimeThreadSuspended`Powiadomienie może wystąpić w dowolnym momencie między [ICorProfilerCallback:: RuntimeSuspendStarted —](icorprofilercallback-runtimesuspendstarted-method.md) i skojarzonymi [ICorProfilerCallback:: RuntimeResumeStarted —](icorprofilercallback-runtimeresumestarted-method.md) wywołaniami zwrotnymi. Powiadomienia, które wystąpiły między [ICorProfilerCallback:: RuntimeSuspendFinished —](icorprofilercallback-runtimesuspendfinished-method.md) i `RuntimeResumeStarted` są dla wątków, które były uruchomione w kodzie niezarządzanym i zostały zawieszone po wprowadzeniu do środowiska uruchomieniowego.  
  
 Ogólnie rzecz biorąc to wywołanie zwrotne występuje zaraz po wstrzymaniu wątku. Jeśli jednak aktualnie wykonywany wątek (wątek, który wywołuje to wywołanie zwrotne) jest zawieszeniem, to wywołanie zwrotne zostanie wykonane tuż przed wstrzymaniem wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [RuntimeThreadResumed, metoda](icorprofilercallback-runtimethreadresumed-method.md)
