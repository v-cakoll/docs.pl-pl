---
title: "ICorProfilerInfo3::GetFunctionLeave3Info — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 04f48562e1ddc07ad1ae166ec44ac7de8afd4312
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="f8092-102">ICorProfilerInfo3::GetFunctionLeave3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8092-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="f8092-103">Zapewnia ramki stosu oraz wartości zwracanej przez funkcję, która jest raportowany przez profiler [functionleave3withinfo — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8092-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="f8092-104">Tę metodę można wywołać tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f8092-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8092-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8092-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8092-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8092-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f8092-107">[in] `FunctionID` Funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="f8092-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="f8092-108">[in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="f8092-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f8092-109">Profiler powinien zawierać takie same `eltInfo` który zostało przekazane do profilera przez [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8092-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="f8092-110">[out] Nieprzezroczystego uchwyt reprezentujący informacje ogólne o ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="f8092-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="f8092-111">Ta dojścia jest prawidłowy tylko w trakcie `FunctionLeave3WithInfo` wywołania zwrotnego o nazwie profilera `GetFunctionLeave3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="f8092-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="f8092-112">[out] Wskaźnik do [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturę, która zawiera wartość, która zostanie zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="f8092-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="f8092-113">Dostęp do informacji zwracanej wartości, `COR_PRF_ENABLE_FUNCTION_RETVAL` musi zostać ustawiona flaga.</span><span class="sxs-lookup"><span data-stu-id="f8092-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="f8092-114">Można użyć profilera [ICorProfilerInfo::SetEventMask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f8092-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8092-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8092-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8092-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8092-116">Requirements</span></span>  
 <span data-ttu-id="f8092-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8092-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8092-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8092-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8092-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8092-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8092-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8092-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8092-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8092-121">See Also</span></span>  
 [<span data-ttu-id="f8092-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f8092-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="f8092-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f8092-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="f8092-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f8092-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="f8092-125">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f8092-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f8092-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f8092-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f8092-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f8092-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
