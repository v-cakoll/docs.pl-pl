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
ms.openlocfilehash: 52988378ff4df0bb03e15c9a4b25efbcd6c318f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457729"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="4cef5-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="4cef5-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="4cef5-103">Określa zaimplementowana profilera funkcji do wywołania w zaktualizowanych wersjach "Wprowadź", "Pozostaw" i "tailcall" punkty zaczepienia w funkcji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4cef5-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cef5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cef5-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cef5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cef5-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="4cef5-106">[in] Wskaźnik do wdrożenia mają być używane jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4cef5-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="4cef5-107">[in] Wskaźnik do wdrożenia mają być używane jako [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4cef5-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="4cef5-108">[in] Wskaźnik do wdrożenia mają być używane jako [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4cef5-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cef5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cef5-109">Remarks</span></span>  
 <span data-ttu-id="4cef5-110">`SetEnterLeaveFunctionHooks2` Metoda jest podobna do [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4cef5-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="4cef5-111">Umożliwia określenie funkcji ma być używany jako nowszych wersji wywołania zwrotne tailcall-enter/pozostaw i drugie określone funkcje, które mają być używane jako starsze wersje wywołania zwrotne tailcall-enter/pozostaw pierwszej.</span><span class="sxs-lookup"><span data-stu-id="4cef5-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="4cef5-112">Jednocześnie może być aktywny tylko jeden zestaw wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="4cef5-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="4cef5-113">W związku z tym jeśli profiler wywołuje zarówno `ICorProfilerInfo::SetEnterLeaveFunctionHooks` i `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` jest używany.</span><span class="sxs-lookup"><span data-stu-id="4cef5-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="4cef5-114">`SetEnterLeaveFunctionHooks2` Metoda może być wywołana tylko z profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4cef5-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cef5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cef5-115">Requirements</span></span>  
 <span data-ttu-id="4cef5-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cef5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cef5-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4cef5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4cef5-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cef5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cef5-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cef5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cef5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cef5-120">See Also</span></span>  
 [<span data-ttu-id="4cef5-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cef5-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="4cef5-122">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cef5-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
