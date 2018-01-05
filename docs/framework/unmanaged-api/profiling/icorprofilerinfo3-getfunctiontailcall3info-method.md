---
title: "ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec36194a11d3d85353c96d4c048d4932071958cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="be29e-102">ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="be29e-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="be29e-103">Udostępnia ramki stosu funkcji, która jest raportowany przez profiler [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="be29e-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="be29e-104">Tę metodę można wywołać tylko podczas `FunctionTailcall3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="be29e-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be29e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="be29e-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be29e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be29e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="be29e-107">[in] `FunctionID` Funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="be29e-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="be29e-108">[in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="be29e-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="be29e-109">Profiler powinien zawierać takie same `eltInfo` który zostało przekazane do profilera przez `FunctionTailcall3WithInfo` funkcji.</span><span class="sxs-lookup"><span data-stu-id="be29e-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="be29e-110">[out] Nieprzezroczystego uchwyt reprezentujący informacje ogólne o ramka stosu danego.</span><span class="sxs-lookup"><span data-stu-id="be29e-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="be29e-111">Ta dojścia jest prawidłowy tylko w trakcie `FunctionTailcall3WithInfo` wywołania zwrotnego o nazwie profilera `GetFunctionTailcall3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="be29e-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be29e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be29e-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be29e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be29e-113">Requirements</span></span>  
 <span data-ttu-id="be29e-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be29e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be29e-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be29e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be29e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be29e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be29e-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be29e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be29e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be29e-118">See Also</span></span>  
 [<span data-ttu-id="be29e-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be29e-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="be29e-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be29e-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="be29e-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="be29e-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="be29e-122">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="be29e-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="be29e-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="be29e-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="be29e-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="be29e-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
