---
title: ICorProfilerCallback::RuntimeSuspendStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865886"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted — Metoda
Powiadamia profiler, że środowisko uruchomieniowe ma wstrzymać wszystkie wątki środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>Parametry  
 `suspendReason`  
 podczas Wartość wyliczenia [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) , która wskazuje przyczynę zawieszenia.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wątki środowiska uruchomieniowego, które znajdują się w kodzie niezarządzanym, mogą kontynuować działanie, dopóki nie spróbują ponownie wprowadzić środowiska uruchomieniowego. W tym momencie zostaną one również zawieszone do momentu wznowienia działania środowiska uruchomieniowego. Dotyczy to również nowych wątków, które wprowadzają środowisko uruchomieniowe. Wszystkie wątki w środowisku uruchomieniowym są zawieszane natychmiast, jeśli znajdują się już w kodzie przerywania lub są proszeni o zawieszenie, gdy osiągną kod przerywania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [RuntimeSuspendAborted, metoda](icorprofilercallback-runtimesuspendaborted-method.md)
- [RuntimeSuspendFinished, metoda](icorprofilercallback-runtimesuspendfinished-method.md)
