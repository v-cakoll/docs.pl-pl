---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c460cfd24a83ca2a6c75e061b7a797c8f455bc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda
Określa zaimplementowana profilera funkcji do wywołania w zaktualizowanych wersjach "Wprowadź", "Pozostaw" i "tailcall" punkty zaczepienia w funkcji zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 [in] Wskaźnik do wdrożenia mają być używane jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego.  
  
 `pFuncLeave`  
 [in] Wskaźnik do wdrożenia mają być używane jako [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołania zwrotnego.  
  
 `pFuncTailcall`  
 [in] Wskaźnik do wdrożenia mają być używane jako [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 `SetEnterLeaveFunctionHooks2` Metoda jest podobna do [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metody. Umożliwia określenie funkcji ma być używany jako nowszych wersji wywołania zwrotne tailcall-enter/pozostaw i drugie określone funkcje, które mają być używane jako starsze wersje wywołania zwrotne tailcall-enter/pozostaw pierwszej.  
  
 Jednocześnie może być aktywny tylko jeden zestaw wywołań zwrotnych. W związku z tym jeśli profiler wywołuje zarówno `ICorProfilerInfo::SetEnterLeaveFunctionHooks` i `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` jest używany.  
  
 `SetEnterLeaveFunctionHooks2` Metoda może być wywołana tylko z profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
