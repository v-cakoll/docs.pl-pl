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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175177"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper — Funkcja
Powiadamia profiler, że dany identyfikator funkcji może być ponownie mapowany na alternatywny identyfikator, który ma być używany w [functionenter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)i [FunctionTailcall2](functiontailcall2-function.md) wywołania zwrotne dla tej funkcji. `FunctionIDMapper`również umożliwia profilera, aby wskazać, czy chce odbierać wywołania zwrotne dla tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[w] Identyfikator funkcji, który ma zostać ponownie zamapowany.

- `pbHookFunction`

  \[out] Wskaźnik do wartości, którą profiler `true` ustawia, jeśli `FunctionEnter2` `FunctionLeave2`chce `FunctionTailcall2` odbierać , i wywołania zwrotne; w przeciwnym razie ustawia `false`tę wartość na .

## <a name="return-value"></a>Wartość zwracana  
 Profiler zwraca wartość, która aparat wykonywania używa jako alternatywny identyfikator funkcji. Zwracana wartość nie `false` może być `pbHookFunction`null, chyba że jest zwracana w . W przeciwnym razie wartość zwracana null spowoduje nieprzewidywalne wyniki, w tym ewentualnie zatrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja `FunctionIDMapper` jest wywołaniem zwrotnym. Jest implementowany przez profiler do ponownego mapowania identyfikatora funkcji do innego identyfikatora, który jest bardziej przydatny dla profilera. Zwraca `FunctionIDMapper` alternatywny identyfikator, który ma być używany dla danej funkcji. Aparat wykonywania następnie honoruje żądanie profilera, przekazując ten alternatywny identyfikator, oprócz tradycyjnego identyfikatora funkcji, `clientData` z `FunctionEnter2`powrotem do profilera w parametrze , `FunctionLeave2`i `FunctionTailcall2` haki, aby zidentyfikować funkcję, dla której hak jest wywoływany.  
  
 Za pomocą metody [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) można określić `FunctionIDMapper` implementację funkcji. `ICorProfilerInfo::SetFunctionIDMapper` Metodę można wywołać tylko raz i zaleca się to zrobić w [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.  
  
 Domyślnie zakłada się, że profiler, który ustawia flagę COR_PRF_MONITOR_ENTERLEAVE za pomocą [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), i który ustawia haki za pośrednictwem [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien odbierać `FunctionEnter2`, `FunctionLeave2`i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji. Jednak profilerzy mogą `FunctionIDMapper` zaimplementować, aby selektywnie unikać `pbHookFunction` odbierania tych wywołań zwrotnych dla niektórych funkcji, ustawiając na `false`.  
  
 Profilerzy powinny być tolerancyjne przypadków, w których wiele wątków profilowane aplikacji są wywołanie tej samej metody/funkcji jednocześnie. W takich przypadkach profiler może `FunctionIDMapper` odbierać wiele `FunctionID`wywołań zwrotnych dla tego samego . Profiler powinien być pewny, aby zwrócić te same wartości z tego `FunctionID`wywołania zwrotnego, gdy jest wywoływana wiele razy z tym samym .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [SetFunctionIDMapper, metoda](icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, funkcja](functionidmapper2-function.md)
- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionLeave2 — Funkcja](functionleave2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
