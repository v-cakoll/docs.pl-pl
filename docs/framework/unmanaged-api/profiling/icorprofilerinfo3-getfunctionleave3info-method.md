---
title: ICorProfilerInfo3::GetFunctionLeave3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d51462017287d42fd468ed0a74a2e83203a3d94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172396"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="b45a0-102">ICorProfilerInfo3::GetFunctionLeave3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="b45a0-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="b45a0-103">Udostępnia ramki stosu i wartość zwracana przez funkcję, która jest zgłaszany do profilera za [functionleave3withinfo — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="b45a0-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="b45a0-104">Ta metoda może być wywoływana tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b45a0-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45a0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b45a0-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b45a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b45a0-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b45a0-107">[in] `FunctionID` Funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="b45a0-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b45a0-108">[in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="b45a0-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b45a0-109">Program profilujący powinien udostępniać takie same `eltInfo` , zostało przekazane do profilera za [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="b45a0-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b45a0-110">[out] Dojście nieprzezroczyste reprezentujący typów ogólnych informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="b45a0-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b45a0-111">Tego dojścia jest prawidłowy tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego, w którym profiler wywołał metodę `GetFunctionLeave3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="b45a0-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="b45a0-112">[out] Wskaźnik do [cor_prf_function_argument_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturę, która zawiera wartość, która jest zwracana przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="b45a0-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="b45a0-113">Dostęp do informacji o wartości zwracanej, `COR_PRF_ENABLE_FUNCTION_RETVAL` musi zostać ustawiona flaga.</span><span class="sxs-lookup"><span data-stu-id="b45a0-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="b45a0-114">Można użyć programu profilującego [icorprofilerinfo::seteventmask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b45a0-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b45a0-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b45a0-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b45a0-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b45a0-116">Requirements</span></span>  
 <span data-ttu-id="b45a0-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45a0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45a0-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b45a0-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b45a0-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b45a0-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b45a0-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b45a0-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b45a0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b45a0-121">See also</span></span>

- [<span data-ttu-id="b45a0-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b45a0-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b45a0-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b45a0-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="b45a0-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b45a0-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b45a0-125">ICorProfilerInfo3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b45a0-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b45a0-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b45a0-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b45a0-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="b45a0-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
