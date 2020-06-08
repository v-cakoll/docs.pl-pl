---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: d40cb424306535cc502d930dd61e6a1e254667da
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496181"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — Metoda
Określa funkcje zaimplementowane przez profiler, które będą wywoływane w podpunktach [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) funkcji zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter3`  
 podczas Wskaźnik do implementacji, który ma być używany jako `FunctionEnter3WithInfo` wywołanie zwrotne.  
  
 `pFuncLeave3`  
 podczas Wskaźnik do implementacji, który ma być używany jako `FunctionLeave3WithInfo` wywołanie zwrotne.  
  
 `pFuncTailcall3`  
 podczas Wskaźnik do implementacji, który ma być używany jako `FunctionTailcall3WithInfo` wywołanie zwrotne.  
  
## <a name="remarks"></a>Uwagi  
 Haki [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) zapewniają inspekcję ramek stosu i argumentów. Aby uzyskać dostęp do tych informacji, należy `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` ustawić flagi, i/lub `COR_PRF_ENABLE_FRAME_INFO` . Profiler może użyć metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń, a następnie użyć `SetEnterLeaveFunctionHooks3WithInfo` metody do zarejestrowania implementacji tej funkcji.  
  
 Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie, a Najnowsza wersja ma pierwszeństwo. W związku z tym, jeśli Profiler wywoła zarówno [SetEnterLeaveFunctionHooks2 —](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) , jak i `SetEnterLeaveFunctionHooks3WithInfo` , `SetEnterLeaveFunctionHooks3WithInfo` jest używany.  
  
 `SetEnterLeaveFunctionHooks3WithInfo`Metoda może być wywoływana tylko z [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Setenterleavefunctionhooks3 —](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
