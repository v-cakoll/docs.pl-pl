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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31766fed66368c044b188b5a58452a5e264a25cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782200"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda
Określa funkcje implementowane przez profiler volat jen tehdy zaktualizowane wersje "enter", "Opuść" i "rekurencja ogonowa" hooks zarządzanej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 [in] Wskaźnik do implementacji, które ma być używany jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego.  
  
 `pFuncLeave`  
 [in] Wskaźnik do implementacji, które ma być używany jako [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołania zwrotnego.  
  
 `pFuncTailcall`  
 [in] Wskaźnik do implementacji, które ma być używany jako [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 `SetEnterLeaveFunctionHooks2` Metoda jest podobna do [icorprofilerinfo::setenterleavefunctionhooks —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metody. Umożliwia określenie funkcji ma być używany jako nowsze wersje wywołania zwrotne enter/leave/tailcall — oraz jego, aby określić funkcje, które ma być używany jako starsze wersje wywołania zwrotne enter/leave/tailcall — w pierwszej.  
  
 W danym momencie może być aktywny tylko jeden zestaw wywołań zwrotnych. W związku z tym jeśli program profilujący wywołuje zarówno `ICorProfilerInfo::SetEnterLeaveFunctionHooks` i `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` jest używany.  
  
 `SetEnterLeaveFunctionHooks2` Metoda może być wywoływana tylko z poziomu programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
