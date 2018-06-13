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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d97b40412b6999000a601b72904a03edf2acd08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454042"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted — Metoda
Powiadamia profilera, że wyszukiwanie została uruchomiona dla funkcji skompilowanego wcześniej przy użyciu Generator obrazu natywnego (NGen.exe).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, dla którego będzie prowadzone wyszukiwanie.  
  
 `pbUseCachedFunction`  
 [out] `true` Jeśli aparat wykonywania powinien używać wersja buforowana funkcji (jeśli jest dostępny); w przeciwnym razie `false`. Jeśli wartość jest `false`, wykonywanie aparatu kompiluje JIT funkcja zamiast wersji, która nie jest skompilowany JIT.  
  
## <a name="remarks"></a>Uwagi  
 W programie .NET Framework w wersji 2.0 `JITCachedFunctionSearchStarted` i [ICorProfilerCallback::JITCachedFunctionSearchFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) wywołania zwrotne nie zostaną wprowadzone dla wszystkich funkcji w regularnych obrazów NGen. Tylko obrazów NGen zoptymalizowane pod kątem profilu wygeneruje wywołań zwrotnych dla wszystkich funkcji w obrazie. Jednak ze względu na dodatkowe obciążenie profiler powinien zażądać zoptymalizowanych pod kątem profilera obrazów NGen tylko, jeśli zamierza użyć tych wywołań zwrotnych, aby wymusić funkcję, która ma być skompilowany just-in-time (JIT). W przeciwnym razie do zbierania informacji o funkcji strategii opóźnieniem należy używać profilera.  
  
 Profilery musi obsługiwać przypadków, w której wiele wątków profilowana aplikacja wywoływania tej samej metody jednocześnie. Na przykład wywołuje wątku A `JITCachedFunctionSearchStarted` i profilera odpowiada ustawiając *pbUseCachedFunction*na FAŁSZ, aby wymusić kompilacji JIT. Wątek, następnie wywołuje [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) i [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Teraz wątków B wywołania `JITCachedFunctionSearchStarted` dla tej samej funkcji. Mimo że profiler stwierdził zamiarze JIT-kompilacji funkcji, profilera odbiera drugi wywołania zwrotnego, ponieważ wątek B wysyła wywołania zwrotnego, zanim profilera odpowiedział na wywołanie wątku A `JITCachedFunctionSearchStarted`. Kolejność, w którym wątków wykonywania wywołań zależy od tego, jak są zaplanowane wątki.  
  
 Profiler odebrania zduplikowane wywołania zwrotne musi ustawić wartość odwołuje się `pbUseCachedFunction` na tę samą wartość dla wszystkich duplikatów wywołań zwrotnych. Oznacza to, gdy `JITCachedFunctionSearchStarted` jest wywołana wiele razy z tym samym `functionId` wartość profilera musi odpowiadać takie same zawsze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
