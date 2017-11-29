---
title: "ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f36a73d26bae96a57d205bb85fa232d16a964dc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="e4456-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4456-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="e4456-103">Określa zaimplementowana profilera funkcje, które będą wywoływane na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4456-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4456-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4456-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4456-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4456-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="e4456-106">[in] Wskaźnik do wdrożenia mają być używane jako `FunctionEnter3` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e4456-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="e4456-107">[in] Wskaźnik do wdrożenia mają być używane jako `FunctionLeave3` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e4456-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="e4456-108">[in] Wskaźnik do wdrożenia mają być używane jako `FunctionTailcall3` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e4456-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4456-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4456-109">Remarks</span></span>  
 <span data-ttu-id="e4456-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) punkty zaczepienia nie udostępniają stosu ramki i argument inspekcji.</span><span class="sxs-lookup"><span data-stu-id="e4456-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="e4456-111">Dostęp do tej informacji `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, i/lub `COR_PRF_ENABLE_FRAME_INFO` flagi muszą być ustawione.</span><span class="sxs-lookup"><span data-stu-id="e4456-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="e4456-112">Profiler można użyć [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić flagi zdarzeń, a następnie użyj [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metodę, aby zarejestrować użytkownika Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4456-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="e4456-113">Tylko jeden zestaw wywołań zwrotnych mogą być aktywne w czasie, a to najnowsza wersja ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="e4456-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="e4456-114">W związku z tym jeśli profiler wywołuje zarówno [SetEnterLeaveFunctionHooks2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3` metody `SetEnterLeaveFunctionHooks3` jest używany.</span><span class="sxs-lookup"><span data-stu-id="e4456-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="e4456-115">`SetEnterLeaveFunctionHooks3` Metoda może być wywołana tylko z profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e4456-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4456-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4456-116">Requirements</span></span>  
 <span data-ttu-id="e4456-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4456-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4456-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4456-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4456-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4456-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4456-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4456-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4456-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4456-121">See Also</span></span>  
 [<span data-ttu-id="e4456-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4456-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="e4456-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="e4456-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="e4456-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="e4456-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="e4456-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="e4456-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="e4456-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4456-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="e4456-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4456-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="e4456-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4456-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="e4456-129">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="e4456-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="e4456-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="e4456-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="e4456-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="e4456-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e4456-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="e4456-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
