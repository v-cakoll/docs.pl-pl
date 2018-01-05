---
title: "ICorProfilerCallback2::GarbageCollectionStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b721b990312f9acda5c9e0208f998793735d2cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="91e97-102">ICorProfilerCallback2::GarbageCollectionStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="91e97-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="91e97-103">Powiadamia profilera kodu rozpoczęto wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="91e97-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91e97-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91e97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91e97-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="91e97-106">[in] Całkowita liczba wpisów w `generationCollected` tablicy.</span><span class="sxs-lookup"><span data-stu-id="91e97-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="91e97-107">[in] Tablica wartości logicznych, które są `true` Jeśli generacji, który odpowiada indeks tablicy jest zebranych przez ten wyrzucanie elementów bezużytecznych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="91e97-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="91e97-108">Tablica jest indeksowany przez wartość [cor_prf_gc_generation —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) wyliczenia, co oznacza generacji.</span><span class="sxs-lookup"><span data-stu-id="91e97-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="91e97-109">[in] Wartość [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) zostało wywołane przez wyliczenie wskazujący przyczynę wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="91e97-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91e97-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91e97-110">Remarks</span></span>  
 <span data-ttu-id="91e97-111">Wszystkie wywołania zwrotne, które odnoszą się do tego wyrzucanie elementów bezużytecznych nastąpi między `GarbageCollectionStarted` wywołania zwrotnego i odpowiadający mu [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="91e97-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="91e97-112">Tych wywołań zwrotnych nie muszą występować na tym samym wątku.</span><span class="sxs-lookup"><span data-stu-id="91e97-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="91e97-113">Bezpiecznie dla profiler do zbadania obiektów w ich oryginalnych lokalizacji podczas `GarbageCollectionStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="91e97-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="91e97-114">Moduł zbierający elementy bezużyteczne rozpocznie się przenoszenie obiektów po powrocie z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="91e97-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="91e97-115">Po profilera zwrócił to wywołanie zwrotne, profilera należy wziąć pod uwagę wszystkie identyfikatory obiektu jest nieprawidłowy, dopóki nie odbierze `ICorProfilerCallback2::GarbageCollectionFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="91e97-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91e97-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91e97-116">Requirements</span></span>  
 <span data-ttu-id="91e97-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91e97-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91e97-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91e97-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91e97-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91e97-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91e97-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91e97-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e97-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91e97-121">See Also</span></span>  
 [<span data-ttu-id="91e97-122">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="91e97-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="91e97-123">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="91e97-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
