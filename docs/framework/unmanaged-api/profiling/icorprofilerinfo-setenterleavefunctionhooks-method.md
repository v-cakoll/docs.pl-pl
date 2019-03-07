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
ms.openlocfilehash: 542ccf384a9b6576e5bce8be1ce9a3dc44c2c71d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473838"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="8046a-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda</span><span class="sxs-lookup"><span data-stu-id="8046a-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="8046a-103">Określa funkcje implementowane przez profiler ma być wywołane na "enter", "Opuść" i "rekurencja ogonowa" hooks zarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8046a-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8046a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8046a-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8046a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8046a-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="8046a-106">[in] Wskaźnik do implementacji, które ma być używany jako [functionenter —](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8046a-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="8046a-107">[in] Wskaźnik do implementacji, które ma być używany jako [functionleave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8046a-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="8046a-108">[in] Wskaźnik do implementacji, które ma być używany jako [functiontailcall —](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8046a-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8046a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8046a-109">Remarks</span></span>  
 <span data-ttu-id="8046a-110">W .NET Framework w wersji 1.0 każdy wskaźnik funkcji może być null powoduje wyłączenie odpowiedniego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8046a-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="8046a-111">Tylko jeden zestaw wywołań zwrotnych, może być aktywne w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="8046a-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="8046a-112">W związku z tym jeśli program profilujący wywołuje zarówno `SetEnterLeaveFunctionHooks` i [icorprofilerinfo2::setenterleavefunctionhooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), następnie `SetEnterLeaveFunctionHooks2` ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="8046a-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="8046a-113">`SetEnterLeaveFunctionHooks` Metoda może być wywołana tylko z poziomu programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8046a-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8046a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8046a-114">Requirements</span></span>  
 <span data-ttu-id="8046a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8046a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8046a-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8046a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8046a-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8046a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8046a-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8046a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8046a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8046a-119">See also</span></span>
- [<span data-ttu-id="8046a-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8046a-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
