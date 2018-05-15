---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f11c11b706dd352d6df0356f2daf91c5417603ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="bc8f3-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc8f3-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="bc8f3-103">Określa zaimplementowana profilera funkcje, które będą wywoływane na [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) punkty zaczepienia zarządzanego funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc8f3-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc8f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc8f3-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="bc8f3-106">[in] Wskaźnik do wdrożenia mają być używane jako `FunctionEnter3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="bc8f3-107">[in] Wskaźnik do wdrożenia mają być używane jako `FunctionLeave3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="bc8f3-108">[in] Wskaźnik do wdrożenia mają być używane jako `FunctionTailcall3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc8f3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc8f3-109">Remarks</span></span>  
 <span data-ttu-id="bc8f3-110">[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) punkty zaczepienia Podaj stosu ramki i argument inspekcji.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="bc8f3-111">Dostęp do tej informacji `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, i/lub `COR_PRF_ENABLE_FRAME_INFO` flagi muszą być ustawione.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="bc8f3-112">Można użyć profilera [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić flagi zdarzeń, a następnie użyj `SetEnterLeaveFunctionHooks3WithInfo` metodę, aby zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bc8f3-113">Tylko jeden zestaw wywołań zwrotnych mogą być aktywne w czasie, a to najnowsza wersja ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="bc8f3-114">W związku z tym jeśli profiler wywołuje zarówno [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` jest używany.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="bc8f3-115">`SetEnterLeaveFunctionHooks3WithInfo` Metoda może być wywołana tylko z profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="bc8f3-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc8f3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc8f3-116">Requirements</span></span>  
 <span data-ttu-id="bc8f3-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc8f3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc8f3-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bc8f3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc8f3-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc8f3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc8f3-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc8f3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8f3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc8f3-121">See Also</span></span>  
 [<span data-ttu-id="bc8f3-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="bc8f3-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="bc8f3-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="bc8f3-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="bc8f3-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="bc8f3-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="bc8f3-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="bc8f3-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="bc8f3-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bc8f3-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="bc8f3-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bc8f3-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="bc8f3-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bc8f3-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="bc8f3-129">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="bc8f3-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 [<span data-ttu-id="bc8f3-130">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc8f3-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="bc8f3-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="bc8f3-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bc8f3-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="bc8f3-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
