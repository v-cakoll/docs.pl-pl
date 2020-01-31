---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 964ea11b8e8c8f494066249f7da2057970d7e8f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866263"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda
Powiadamia profiler o rozpoczęciu wyszukiwania dla funkcji, która została skompilowana wcześniej przy użyciu natywnego generatora obrazu (NGen. exe).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[in) identyfikator funkcji, dla której jest wykonywane wyszukiwanie.

- `pbUseCachedFunction`

  \[out] `true`, jeśli aparat wykonywania powinien używać buforowanej wersji funkcji (jeśli jest dostępna); w przeciwnym razie `false`. Jeśli wartość jest `false`, aparat wykonywania JIT — kompiluje funkcję zamiast korzystania z wersji, która nie jest skompilowana przez JIT.

## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersji 2,0 metody wywołania zwrotne `JITCachedFunctionSearchStarted` i [ICorProfilerCallback:: JITCachedFunctionSearchFinished —](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) nie będą wykonywane dla wszystkich funkcji w zwykłych obrazach Ngen. Tylko obrazy NGen zoptymalizowane pod kątem profilu generują wywołania zwrotne dla wszystkich funkcji w obrazie. Jednak ze względu na dodatkowe obciążenie, profiler powinien zażądać obrazów NGen zoptymalizowanych pod kątem profilera tylko wtedy, gdy zamierza użyć tych wywołań zwrotnych w celu wymuszenia skompilowania funkcji just-in-Time (JIT). W przeciwnym razie Profiler powinien używać strategii z opóźnieniem do zbierania informacji o funkcji.  
  
 Profilowani muszą obsługiwać przypadki, w których wiele wątków profilowanej aplikacji wywołuje tę samą metodę jednocześnie. Na przykład wywołania wątku A `JITCachedFunctionSearchStarted` i profilera reagują przez ustawienie *pbUseCachedFunction*na false, aby wymusić kompilację JIT. Wątek A następnie wywołuje [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) i [ICorProfilerCallback:: JITCompilationFinished —](icorprofilercallback-jitcompilationfinished-method.md).  
  
 Teraz wątek B wywołuje `JITCachedFunctionSearchStarted` dla tej samej funkcji. Mimo że profiler stwierdził, że zamiaru JIT-kompiluje funkcję, profiler odbiera drugie wywołanie zwrotne, ponieważ wątek B wysyła wywołanie zwrotne, zanim profiler odpowiedział na wywołanie wątku A do `JITCachedFunctionSearchStarted`. Kolejność, w jakiej wątki powodują wywołania, zależy od tego, jak wątki są zaplanowane.  
  
 Gdy profiler odbiera zduplikowane wywołania zwrotne, musi ustawić wartość, do której odwołuje się `pbUseCachedFunction`, na tę samą wartość dla wszystkich zduplikowanych wywołań zwrotnych. Oznacza to, że gdy `JITCachedFunctionSearchStarted` jest wywoływana wielokrotnie z tą samą wartością `functionId`, profiler musi odpowiedzieć na ten sam czas.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
