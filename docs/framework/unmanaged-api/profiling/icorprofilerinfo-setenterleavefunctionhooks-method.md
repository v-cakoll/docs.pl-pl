---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58e7b3e76d90e9e43f3f5259c52b52cd9f8e1f6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455078"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda
Określa zaimplementowana profilera funkcji do wywołania "Wprowadź", "Pozostaw" i "tailcall" punkty zaczepienia w funkcji zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 [in] Wskaźnik do wdrożenia mają być używane jako [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) wywołania zwrotnego.  
  
 `pFuncLeave`  
 [in] Wskaźnik do wdrożenia mają być używane jako [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołania zwrotnego.  
  
 `pFuncTailcall`  
 [in] Wskaźnik do wdrożenia mają być używane jako [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 W programie .NET Framework w wersji 1.0 każdy wskaźnik funkcji może być null powoduje wyłączenie odpowiedniej wywołanie zwrotne.  
  
 Jednocześnie może być aktywny tylko jeden zestaw wywołań zwrotnych. W związku z tym jeśli profiler wywołuje zarówno `SetEnterLeaveFunctionHooks` i [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), następnie `SetEnterLeaveFunctionHooks2` pierwszeństwo.  
  
 `SetEnterLeaveFunctionHooks` Metodę można wywołać tylko z profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
