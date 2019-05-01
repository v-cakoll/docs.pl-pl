---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73321a28b1c61775d08e2c60ee2b9a863b8250dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000561"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="9acc9-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="9acc9-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="9acc9-103">Określa funkcje implementowane przez program profilujący zostanie wywołana na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="9acc9-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9acc9-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9acc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9acc9-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="9acc9-106">[in] Wskaźnik do implementacji, które ma być używany jako `FunctionEnter3` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9acc9-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="9acc9-107">[in] Wskaźnik do implementacji, które ma być używany jako `FunctionLeave3` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9acc9-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="9acc9-108">[in] Wskaźnik do implementacji, które ma być używany jako `FunctionTailcall3` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9acc9-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9acc9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9acc9-109">Remarks</span></span>  
 <span data-ttu-id="9acc9-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) punkty zaczepienia. nie wpisuj stosu ramki i argument inspekcji.</span><span class="sxs-lookup"><span data-stu-id="9acc9-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="9acc9-111">Dostęp do tych informacji do `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, i/lub `COR_PRF_ENABLE_FRAME_INFO` flagi, które muszą być ustawione.</span><span class="sxs-lookup"><span data-stu-id="9acc9-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="9acc9-112">Można użyć programu profilującego [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić flagi zdarzenia, a następnie użyj [icorprofilerinfo3::setenterleavefunctionhooks3withinfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metodę, aby zarejestrować swoje Implementacja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9acc9-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="9acc9-113">Tylko jeden zestaw wywołań zwrotnych, może być aktywny w danym momencie, a najnowsza wersja ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="9acc9-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="9acc9-114">W związku z tym jeśli program profilujący wywołuje zarówno [setenterleavefunctionhooks2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3` metody `SetEnterLeaveFunctionHooks3` jest używany.</span><span class="sxs-lookup"><span data-stu-id="9acc9-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="9acc9-115">`SetEnterLeaveFunctionHooks3` Metoda może być wywoływana tylko z poziomu programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9acc9-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9acc9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9acc9-116">Requirements</span></span>  
 <span data-ttu-id="9acc9-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9acc9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9acc9-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9acc9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9acc9-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9acc9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9acc9-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9acc9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acc9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9acc9-121">See also</span></span>

- [<span data-ttu-id="9acc9-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9acc9-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="9acc9-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="9acc9-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="9acc9-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="9acc9-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="9acc9-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="9acc9-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="9acc9-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9acc9-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="9acc9-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9acc9-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="9acc9-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9acc9-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="9acc9-129">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="9acc9-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="9acc9-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="9acc9-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9acc9-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="9acc9-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9acc9-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="9acc9-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
