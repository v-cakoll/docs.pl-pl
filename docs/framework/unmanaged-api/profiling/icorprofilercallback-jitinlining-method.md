---
title: ICorProfilerCallback::JITInlining — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866218"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining — Metoda
Powiadamia profiler, że kompilator just in Time (JIT) ma wstawić funkcję w wierszu z inną funkcją.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parametry  
 `callerId`  
 podczas Identyfikator funkcji, w której zostanie wstawiona funkcja `calleeId`.  
  
 `calleeId`  
 podczas Identyfikator funkcji, która ma zostać wstawiona.  
  
 `pfShouldInline`  
 [out] `true`, aby zezwolić na wstawianie; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Profiler może ustawić `pfShouldInline` na `false`, aby uniemożliwić Wstawianie funkcji `calleeId` do funkcji `callerId`. Dodatkowo profiler może globalnie wyłączyć wstawianie wbudowane przy użyciu wartości COR_PRF_DISABLE_INLINING [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Enumeration.  
  
 Wbudowane funkcje nie zgłaszają zdarzeń do wprowadzenia lub opuszczenia. W związku z tym profiler musi ustawić `pfShouldInline`, aby `false` w celu wygenerowania dokładnej wykres wywołań. Ustawienie `pfShouldInline` na `false` będzie miało wpływ na wydajność, ponieważ Wstawianie wbudowane zwykle zwiększa szybkość i zmniejsza liczbę oddzielnych zdarzeń kompilacji JIT dla włożonej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
