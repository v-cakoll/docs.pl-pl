---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: ad155c4efb9f11565eeed8bc0a3540311aca4eb7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866276"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished — Metoda
Powiadamia profiler o zakończeniu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu natywnego generatora obrazu (NGen. exe).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[in) identyfikator funkcji, dla której wykonano wyszukiwanie.

- `result`

  \[w] wartość wyliczenia [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) , która wskazuje wynik wyszukiwania.

## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersji 2,0, wywołania zwrotne [ICorProfilerCallback:: JITCachedFunctionSearchStarted —](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) i `JITCachedFunctionSearchFinished` nie będą wykonywane dla wszystkich funkcji w zwykłych obrazach Ngen. Tylko obrazy NGen zoptymalizowane pod kątem profilera generują wywołania zwrotne dla wszystkich funkcji w obrazie. Jednak ze względu na dodatkowe obciążenie, profiler powinien zażądać obrazów NGen zoptymalizowanych pod kątem profilera tylko wtedy, gdy zamierza użyć tych wywołań zwrotnych w celu wymuszenia skompilowania funkcji just-in-Time (JIT). W przeciwnym razie Profiler powinien używać strategii z opóźnieniem do zbierania informacji o funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
