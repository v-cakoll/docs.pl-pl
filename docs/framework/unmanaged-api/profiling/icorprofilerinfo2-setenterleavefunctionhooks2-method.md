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
ms.openlocfilehash: 4068c8fee13a6086bc6b48bcc6d4117357062747
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449787"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="faf9f-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="faf9f-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="faf9f-103">Określa funkcje zaimplementowane dla profilera, które mają być wywoływane na zaktualizowanych podpunktach "Enter", "urlop" i "tailcall" funkcji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="faf9f-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="faf9f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faf9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="faf9f-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="faf9f-106">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="faf9f-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="faf9f-107">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="faf9f-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="faf9f-108">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="faf9f-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf9f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faf9f-109">Remarks</span></span>  
 <span data-ttu-id="faf9f-110">Metoda `SetEnterLeaveFunctionHooks2` jest podobna do metody [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="faf9f-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="faf9f-111">Użyj tej funkcji, aby określić funkcje, które mają być używane jako nowsze wersje wywołania zwrotnego Enter/opuścić/tailcall, a drugie, aby określić funkcje, które mają być używane jako starsze wersje wywołania zwrotnego Enter/opuścić/tailcall.</span><span class="sxs-lookup"><span data-stu-id="faf9f-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="faf9f-112">Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="faf9f-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="faf9f-113">W tym przypadku, jeśli Profiler wywoła zarówno `ICorProfilerInfo::SetEnterLeaveFunctionHooks`, jak i `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` jest używany.</span><span class="sxs-lookup"><span data-stu-id="faf9f-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="faf9f-114">Metodę `SetEnterLeaveFunctionHooks2` można wywołać tylko z [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego profilera.</span><span class="sxs-lookup"><span data-stu-id="faf9f-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf9f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="faf9f-115">Requirements</span></span>  
 <span data-ttu-id="faf9f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf9f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf9f-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="faf9f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="faf9f-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="faf9f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faf9f-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faf9f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf9f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf9f-120">See also</span></span>

- [<span data-ttu-id="faf9f-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="faf9f-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="faf9f-122">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="faf9f-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
