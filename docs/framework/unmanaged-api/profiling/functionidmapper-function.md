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
ms.openlocfilehash: afc818dfe625bfc329ceb1660539eb119702a90d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500679"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper — Funkcja
Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)i [FunctionTailcall2](functiontailcall2-function.md) dla tej funkcji. `FunctionIDMapper`umożliwia również profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[w] identyfikator funkcji, która ma zostać ponownie zmapowana.

- `pbHookFunction`

  \[out] wskaźnik do wartości, która jest ustawiana przez profiler `true` , jeśli chce otrzymywać `FunctionEnter2` , `FunctionLeave2` i `FunctionTailcall2` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false` .

## <a name="return-value"></a>Wartość zwracana  
 Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji. Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction` . W przeciwnym razie wartość zwracana null będzie generować nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 `FunctionIDMapper`Funkcja jest wywołaniem zwrotnym. Jest implementowany przez profiler, aby ponownie mapować identyfikator funkcji na inny identyfikator, który jest bardziej przydatny dla profilera. `FunctionIDMapper`Zwraca alternatywny identyfikator, który ma być używany dla danej funkcji. Aparat wykonywania następnie będzie przestrzegać żądania profilera przez przekazanie tego alternatywnego identyfikatora, oprócz tradycyjnego identyfikatora funkcji, Wróć do profilera w `clientData` parametrze `FunctionEnter2` , `FunctionLeave2` , i `FunctionTailcall2` punkty zaczepienia, aby zidentyfikować funkcję, dla której jest wywoływany element Hook.  
  
 Aby określić implementację funkcji, można użyć metody [ICorProfilerInfo:: SetFunctionIDMapper —](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` . Metodę można wywołać `ICorProfilerInfo::SetFunctionIDMapper` tylko raz i zalecamy wykonanie tego w [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
 Domyślnie zakłada się, że profiler ustawiający flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)i który ustawia punkty zaczepienia za pośrednictwem [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien otrzymać `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` wywołania zwrotne, i dla każdej funkcji. Jednakże można zaimplementować program `FunctionIDMapper` do tworzenia, aby selektywnie unikać otrzymywania wywołania zwrotnego dla niektórych funkcji przez ustawienie `pbHookFunction` do `false` .  
  
 Profilowani powinni być odporne na uszkodzenia przypadków, w których wiele wątków profilowanej aplikacji jednocześnie wywołuje tę samą metodę/funkcję. W takich przypadkach profiler może odbierać wiele `FunctionIDMapper` wywołań zwrotnych dla tego samego `FunctionID` . Profiler powinien mieć pewność, że zwracają te same wartości z tego wywołania zwrotnego, gdy jest wywoływana wiele razy z tym samym `FunctionID` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [SetFunctionIDMapper, metoda](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, funkcja](functionidmapper2-function.md)
- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionLeave2 — Funkcja](functionleave2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
