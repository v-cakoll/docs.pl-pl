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
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="caad9-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="caad9-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="caad9-103">Określa funkcje implementowane przez profiler volat jen tehdy zaktualizowane wersje "enter", "Opuść" i "rekurencja ogonowa" hooks zarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="caad9-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caad9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="caad9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caad9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="caad9-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="caad9-106">[in] Wskaźnik do implementacji, które ma być używany jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="caad9-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="caad9-107">[in] Wskaźnik do implementacji, które ma być używany jako [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="caad9-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="caad9-108">[in] Wskaźnik do implementacji, które ma być używany jako [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="caad9-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caad9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="caad9-109">Remarks</span></span>  
 <span data-ttu-id="caad9-110">`SetEnterLeaveFunctionHooks2` Metoda jest podobna do [icorprofilerinfo::setenterleavefunctionhooks —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="caad9-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="caad9-111">Umożliwia określenie funkcji ma być używany jako nowsze wersje wywołania zwrotne enter/leave/tailcall — oraz jego, aby określić funkcje, które ma być używany jako starsze wersje wywołania zwrotne enter/leave/tailcall — w pierwszej.</span><span class="sxs-lookup"><span data-stu-id="caad9-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="caad9-112">W danym momencie może być aktywny tylko jeden zestaw wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="caad9-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="caad9-113">W związku z tym jeśli program profilujący wywołuje zarówno `ICorProfilerInfo::SetEnterLeaveFunctionHooks` i `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` jest używany.</span><span class="sxs-lookup"><span data-stu-id="caad9-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="caad9-114">`SetEnterLeaveFunctionHooks2` Metoda może być wywoływana tylko z poziomu programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="caad9-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caad9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="caad9-115">Requirements</span></span>  
 <span data-ttu-id="caad9-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caad9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caad9-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="caad9-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="caad9-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caad9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caad9-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caad9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caad9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caad9-120">See also</span></span>

- [<span data-ttu-id="caad9-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="caad9-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="caad9-122">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="caad9-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
