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
ms.openlocfilehash: da3e51174d0b11f5cc706b7680048da519e2ed3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049495"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="ea88b-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea88b-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="ea88b-103">Określa funkcje implementowane przez program profilujący zostanie wywołana na [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) punkty zaczepienia funkcji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="ea88b-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea88b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea88b-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea88b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea88b-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="ea88b-106">[in] Wskaźnik do implementacji, które ma być używany jako `FunctionEnter3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ea88b-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="ea88b-107">[in] Wskaźnik do implementacji, które ma być używany jako `FunctionLeave3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ea88b-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="ea88b-108">[in] Wskaźnik do implementacji, które ma być używany jako `FunctionTailcall3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ea88b-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea88b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea88b-109">Remarks</span></span>  
 <span data-ttu-id="ea88b-110">[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) punkty zaczepienia zapewniają stosu ramki i argument inspekcji.</span><span class="sxs-lookup"><span data-stu-id="ea88b-110">The [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="ea88b-111">Dostęp do tych informacji do `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, i/lub `COR_PRF_ENABLE_FRAME_INFO` flagi, które muszą być ustawione.</span><span class="sxs-lookup"><span data-stu-id="ea88b-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="ea88b-112">Można użyć programu profilującego [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby ustawić flagi zdarzenia, a następnie użyj `SetEnterLeaveFunctionHooks3WithInfo` metodę, aby zarejestrować implementacji tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ea88b-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ea88b-113">Tylko jeden zestaw wywołań zwrotnych, może być aktywny w danym momencie, a najnowsza wersja ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="ea88b-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="ea88b-114">W związku z tym jeśli program profilujący wywołuje zarówno [setenterleavefunctionhooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` jest używany.</span><span class="sxs-lookup"><span data-stu-id="ea88b-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="ea88b-115">`SetEnterLeaveFunctionHooks3WithInfo` Metoda może być wywoływana tylko z poziomu programu profilującego [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ea88b-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea88b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea88b-116">Requirements</span></span>  
 <span data-ttu-id="ea88b-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea88b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea88b-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea88b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea88b-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea88b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea88b-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea88b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea88b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea88b-121">See also</span></span>

- [<span data-ttu-id="ea88b-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="ea88b-122">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="ea88b-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ea88b-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="ea88b-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ea88b-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="ea88b-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="ea88b-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="ea88b-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ea88b-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="ea88b-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ea88b-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="ea88b-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ea88b-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="ea88b-129">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="ea88b-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="ea88b-130">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea88b-130">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ea88b-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ea88b-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ea88b-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="ea88b-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
