---
title: "ICorProfilerInfo2::GetObjectGeneration — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e90139f96638dbb1a183f98e754838ff52424fc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="ed5c1-102">ICorProfilerInfo2::GetObjectGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed5c1-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="ed5c1-103">Pobiera segment stosu, który zawiera określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="ed5c1-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed5c1-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed5c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed5c1-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="ed5c1-106">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="ed5c1-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="ed5c1-107">[out] Wskaźnik do [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, która opisuje zakresu (Blokuj) pamięci w ramach wybranej generacji jest poddawana wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ed5c1-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="ed5c1-108">Ten zakres zawiera określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="ed5c1-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed5c1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed5c1-109">Remarks</span></span>  
 <span data-ttu-id="ed5c1-110">`GetObjectGeneration` Zwrotne profilera, może zostać wywołana metoda pod warunkiem, że pamięci nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="ed5c1-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="ed5c1-111">Oznacza to, może być wywoływana z dowolnego wywołania zwrotnego z wyjątkiem tych, które mają miejsce między [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="ed5c1-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed5c1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed5c1-112">Requirements</span></span>  
 <span data-ttu-id="ed5c1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed5c1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed5c1-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed5c1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed5c1-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed5c1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed5c1-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed5c1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5c1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed5c1-117">See Also</span></span>  
 [<span data-ttu-id="ed5c1-118">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="ed5c1-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ed5c1-119">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ed5c1-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
