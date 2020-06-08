---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 78489aae840ff17e68b10bd7593fb7be4dae1af7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496740"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda
Określa funkcje zaimplementowane dla profilera, które mają być wywoływane na zaktualizowanych podpunktach "Enter", "urlop" i "tailcall" funkcji zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionEnter2](functionenter2-function.md) .  
  
 `pFuncLeave`  
 podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionLeave2](functionleave2-function.md) .  
  
 `pFuncTailcall`  
 podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionTailcall2](functiontailcall2-function.md) .  
  
## <a name="remarks"></a>Uwagi  
 `SetEnterLeaveFunctionHooks2`Metoda jest podobna do metody [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](icorprofilerinfo-setenterleavefunctionhooks-method.md) . Użyj tej funkcji, aby określić funkcje, które mają być używane jako nowsze wersje wywołania zwrotnego Enter/opuścić/tailcall, a drugie, aby określić funkcje, które mają być używane jako starsze wersje wywołania zwrotnego Enter/opuścić/tailcall.  
  
 Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie. W takim przypadku, jeśli Profiler wywołuje `ICorProfilerInfo::SetEnterLeaveFunctionHooks` zarówno `SetEnterLeaveFunctionHooks2` , jak i, `SetEnterLeaveFunctionHooks2` jest używany.  
  
 `SetEnterLeaveFunctionHooks2`Metoda może być wywoływana tylko z [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
