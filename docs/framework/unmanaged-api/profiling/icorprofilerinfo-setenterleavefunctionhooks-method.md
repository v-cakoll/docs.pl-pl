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
ms.openlocfilehash: 1b6f53d5747eca00b898b2cde66d75764ca490cf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772108"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="919ff-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda</span><span class="sxs-lookup"><span data-stu-id="919ff-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="919ff-103">Określa funkcje implementowane przez profiler ma być wywołane na "enter", "Opuść" i "rekurencja ogonowa" hooks zarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="919ff-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="919ff-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="919ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="919ff-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="919ff-106">[in] Wskaźnik do implementacji, które ma być używany jako [functionenter —](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="919ff-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="919ff-107">[in] Wskaźnik do implementacji, które ma być używany jako [functionleave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="919ff-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="919ff-108">[in] Wskaźnik do implementacji, które ma być używany jako [functiontailcall —](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="919ff-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="919ff-109">Remarks</span></span>  
 <span data-ttu-id="919ff-110">W .NET Framework w wersji 1.0 każdy wskaźnik funkcji może być null powoduje wyłączenie odpowiedniego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="919ff-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="919ff-111">Tylko jeden zestaw wywołań zwrotnych, może być aktywne w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="919ff-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="919ff-112">W związku z tym jeśli program profilujący wywołuje zarówno `SetEnterLeaveFunctionHooks` i [icorprofilerinfo2::setenterleavefunctionhooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), następnie `SetEnterLeaveFunctionHooks2` ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="919ff-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="919ff-113">`SetEnterLeaveFunctionHooks` Metoda może być wywołana tylko z poziomu programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="919ff-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919ff-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="919ff-114">Requirements</span></span>  
 <span data-ttu-id="919ff-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919ff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919ff-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="919ff-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="919ff-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="919ff-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="919ff-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919ff-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="919ff-119">See also</span></span>

- [<span data-ttu-id="919ff-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="919ff-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
