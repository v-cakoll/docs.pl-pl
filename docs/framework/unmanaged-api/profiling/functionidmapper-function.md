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
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866947"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper — Funkcja
Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)i [FunctionTailcall2](functiontailcall2-function.md) dla tej funkcji. `FunctionIDMapper` również umożliwia profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[] identyfikator funkcji, która ma zostać ponownie zmapowana.

- `pbHookFunction`

  \[out] wskaźnik do wartości, która jest ustawiana przez profiler `true`, jeśli chce otrzymywać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.

## <a name="return-value"></a>Wartość zwrócona  
 Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji. Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction`. W przeciwnym razie wartość zwracana null będzie generować nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja `FunctionIDMapper` jest wywołaniem zwrotnym. Jest implementowany przez profiler, aby ponownie mapować identyfikator funkcji na inny identyfikator, który jest bardziej przydatny dla profilera. `FunctionIDMapper` zwraca alternatywny identyfikator, który ma być używany dla danej funkcji. Aparat wykonywania następnie będzie przestrzegać żądania profilera przez przekazanie tego alternatywnego identyfikatora, oprócz tradycyjnego identyfikatora funkcji, z powrotem do profilera w `clientData` parametr `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` punkty zaczepienia, aby zidentyfikować funkcję, dla której jest wywoływany element Hook.  
  
 Aby określić implementację funkcji `FunctionIDMapper`, można użyć metody [ICorProfilerInfo:: SetFunctionIDMapper —](icorprofilerinfo-setfunctionidmapper-method.md) . Metodę `ICorProfilerInfo::SetFunctionIDMapper` można wywołać tylko raz i zalecamy wykonanie tego w [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
 Domyślnie zakłada się, że profiler ustawiający flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)i który ustawia haki za pośrednictwem [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien otrzymać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji. Jednakże można zaimplementować program do `FunctionIDMapper`, aby selektywnie unikać otrzymywania wywołania zwrotnego dla niektórych funkcji przez ustawienie `pbHookFunction` do `false`.  
  
 Profilowani powinni być odporne na uszkodzenia przypadków, w których wiele wątków profilowanej aplikacji jednocześnie wywołuje tę samą metodę/funkcję. W takich przypadkach profiler może odbierać wiele wywołań zwrotnych `FunctionIDMapper` dla tego samego `FunctionID`. Profiler powinien mieć pewność, że zwracają te same wartości z tego wywołania zwrotnego, gdy jest wywoływana wiele razy z tą samą `FunctionID`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [SetFunctionIDMapper, metoda](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, funkcja](functionidmapper2-function.md)
- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionLeave2, funkcja](functionleave2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
