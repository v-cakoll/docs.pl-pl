---
title: FunctionIDMapper — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440704"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper — Funkcja
Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) dla tej funkcji. `FunctionIDMapper` również umożliwia profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 podczas Identyfikator funkcji, która ma zostać ponownie zmapowana.  
  
 `pbHookFunction`  
 określoną Wskaźnik do wartości, którą profiler ustawia do `true`, jeśli chce otrzymywać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji. Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction`. W przeciwnym razie wartość zwracana null będzie generować nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja `FunctionIDMapper` jest wywołaniem zwrotnym. Jest implementowany przez profiler, aby ponownie mapować identyfikator funkcji na inny identyfikator, który jest bardziej przydatny dla profilera. `FunctionIDMapper` zwraca alternatywny identyfikator, który ma być używany dla danej funkcji. Aparat wykonywania następnie będzie przestrzegać żądania profilera przez przekazanie tego alternatywnego identyfikatora, oprócz tradycyjnego identyfikatora funkcji, z powrotem do profilera w `clientData` parametr `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` punkty zaczepienia, aby zidentyfikować funkcję, dla której jest wywoływany element Hook.  
  
 Aby określić implementację funkcji `FunctionIDMapper`, można użyć metody [ICorProfilerInfo:: SetFunctionIDMapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) . Metodę `ICorProfilerInfo::SetFunctionIDMapper` można wywołać tylko raz i zalecamy wykonanie tego w [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
 Domyślnie zakłada się, że profiler ustawiający flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)i który ustawia haki za pośrednictwem [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien otrzymać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji. Jednakże można zaimplementować program do `FunctionIDMapper`, aby selektywnie unikać otrzymywania wywołania zwrotnego dla niektórych funkcji przez ustawienie `pbHookFunction` do `false`.  
  
 Profilowani powinni być odporne na uszkodzenia przypadków, w których wiele wątków profilowanej aplikacji jednocześnie wywołuje tę samą metodę/funkcję. W takich przypadkach profiler może odbierać wiele wywołań zwrotnych `FunctionIDMapper` dla tego samego `FunctionID`. Profiler powinien mieć pewność, że zwracają te same wartości z tego wywołania zwrotnego, gdy jest wywoływana wiele razy z tą samą `FunctionID`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [SetFunctionIDMapper, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
