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
ms.openlocfilehash: 7eac42e1d8132ca9e6d6c6b43efd43b88c1e5d3d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868586"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="1af93-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="1af93-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="1af93-103">Określa funkcje zaimplementowane dla profilera, które mają być wywoływane na zaktualizowanych podpunktach "Enter", "urlop" i "tailcall" funkcji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="1af93-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1af93-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1af93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1af93-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="1af93-106">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1af93-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="1af93-107">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionLeave2](functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1af93-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="1af93-108">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionTailcall2](functiontailcall2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1af93-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1af93-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1af93-109">Remarks</span></span>  
 <span data-ttu-id="1af93-110">Metoda `SetEnterLeaveFunctionHooks2` jest podobna do metody [ICorProfilerInfo:: SetEnterLeaveFunctionHooks —](icorprofilerinfo-setenterleavefunctionhooks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1af93-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="1af93-111">Użyj tej funkcji, aby określić funkcje, które mają być używane jako nowsze wersje wywołania zwrotnego Enter/opuścić/tailcall, a drugie, aby określić funkcje, które mają być używane jako starsze wersje wywołania zwrotnego Enter/opuścić/tailcall.</span><span class="sxs-lookup"><span data-stu-id="1af93-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="1af93-112">Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="1af93-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="1af93-113">W tym przypadku, jeśli Profiler wywoła zarówno `ICorProfilerInfo::SetEnterLeaveFunctionHooks`, jak i `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` jest używany.</span><span class="sxs-lookup"><span data-stu-id="1af93-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="1af93-114">Metodę `SetEnterLeaveFunctionHooks2` można wywołać tylko z [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego profilera.</span><span class="sxs-lookup"><span data-stu-id="1af93-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1af93-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1af93-115">Requirements</span></span>  
 <span data-ttu-id="1af93-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1af93-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1af93-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1af93-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1af93-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1af93-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1af93-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1af93-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af93-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1af93-120">See also</span></span>

- [<span data-ttu-id="1af93-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1af93-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1af93-122">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1af93-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
