---
title: "ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2bf897ce41e2d9a8b4c7b9eeb4053ea0e9ad951
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="8c837-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c837-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="8c837-103">Określa zaimplementowana profilera funkcji do wywołania "Wprowadź", "Pozostaw" i "tailcall" punkty zaczepienia w funkcji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8c837-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c837-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c837-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c837-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="8c837-106">[in] Wskaźnik do wdrożenia mają być używane jako [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8c837-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="8c837-107">[in] Wskaźnik do wdrożenia mają być używane jako [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8c837-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="8c837-108">[in] Wskaźnik do wdrożenia mają być używane jako [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8c837-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c837-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c837-109">Remarks</span></span>  
 <span data-ttu-id="8c837-110">W programie .NET Framework w wersji 1.0 każdy wskaźnik funkcji może być null powoduje wyłączenie odpowiedniej wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="8c837-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="8c837-111">Jednocześnie może być aktywny tylko jeden zestaw wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="8c837-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="8c837-112">W związku z tym jeśli profiler wywołuje zarówno `SetEnterLeaveFunctionHooks` i [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), następnie `SetEnterLeaveFunctionHooks2` pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="8c837-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="8c837-113">`SetEnterLeaveFunctionHooks` Metodę można wywołać tylko z profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8c837-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c837-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c837-114">Requirements</span></span>  
 <span data-ttu-id="8c837-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c837-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c837-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c837-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c837-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c837-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c837-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c837-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c837-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c837-119">See Also</span></span>  
 [<span data-ttu-id="8c837-120">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="8c837-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
