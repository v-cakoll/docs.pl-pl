---
title: ICorProfilerInfo2::GetObjectGeneration — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 729ae390d36f82cbafd46385b396d6513489628e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474807"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="ce34a-102">ICorProfilerInfo2::GetObjectGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce34a-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="ce34a-103">Pobiera segment stosu, który zawiera dany obiekt.</span><span class="sxs-lookup"><span data-stu-id="ce34a-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce34a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce34a-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce34a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce34a-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="ce34a-106">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="ce34a-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="ce34a-107">[out] Wskaźnik do [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, która opisuje zakresu (Blokuj) pamięci w generacji, która jest w trakcie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ce34a-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="ce34a-108">Ten zakres zawiera określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="ce34a-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce34a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce34a-109">Remarks</span></span>  
 <span data-ttu-id="ce34a-110">`GetObjectGeneration` Metoda może być wywoływana z dowolnym zwrotnego profilera, pod warunkiem, że wyrzucanie elementów bezużytecznych nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="ce34a-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="ce34a-111">Oznacza to, może być wywoływana z dowolnego wywołania zwrotnego, z wyjątkiem tych, które mają miejsce między [icorprofilercallback2::garbagecollectionstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="ce34a-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce34a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce34a-112">Requirements</span></span>  
 <span data-ttu-id="ce34a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce34a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce34a-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce34a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce34a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce34a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce34a-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce34a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce34a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce34a-117">See also</span></span>
- [<span data-ttu-id="ce34a-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce34a-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="ce34a-119">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce34a-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
