---
title: ICorProfilerCallback2::GarbageCollectionStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5f9104dded44540c47c955c15354d8d76a27650
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183076"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="03107-102">ICorProfilerCallback2::GarbageCollectionStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="03107-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="03107-103">Powiadamia program profilujący kodu uruchomienia wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="03107-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03107-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03107-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03107-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03107-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="03107-106">[in] Łączna liczba wpisów w `generationCollected` tablicy.</span><span class="sxs-lookup"><span data-stu-id="03107-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="03107-107">[in] Tablica wartości logicznych, które są `true` Jeśli generacji, która odnosi się do indeksu tablicy jest zebranych przez ten wyrzucania elementów bezużytecznych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="03107-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="03107-108">Tablica jest indeksowana przez wartość [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) wyliczenia, co oznacza jego generacji.</span><span class="sxs-lookup"><span data-stu-id="03107-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="03107-109">[in] Wartość [cor_prf_gc_reason —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) wyliczenia, która wskazuje przyczynę wyrzucania elementów bezużytecznych zostało wywołane.</span><span class="sxs-lookup"><span data-stu-id="03107-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03107-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03107-110">Remarks</span></span>  
 <span data-ttu-id="03107-111">Wszystkie wywołania zwrotne, które odnoszą się do tego wyrzucania elementów bezużytecznych nastąpi między `GarbageCollectionStarted` wywołania zwrotnego i odpowiedni [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03107-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="03107-112">Te wywołania zwrotne nie muszą występować na tym samym wątku.</span><span class="sxs-lookup"><span data-stu-id="03107-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="03107-113">Bezpiecznie programu Profiler sprawdzić obiektów w ich oryginalnej lokalizacji podczas `GarbageCollectionStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03107-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="03107-114">Moduł zbierający elementy bezużyteczne rozpocznie poruszających się obiektów po powrocie z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="03107-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="03107-115">Po program profilujący został zwrócony z to wywołanie zwrotne, program profilujący należy wziąć pod uwagę wszystkie identyfikatory obiektu jest nieprawidłowy, dopóki nie odbierze `ICorProfilerCallback2::GarbageCollectionFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03107-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03107-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03107-116">Requirements</span></span>  
 <span data-ttu-id="03107-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03107-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03107-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03107-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03107-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03107-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03107-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03107-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03107-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03107-121">See also</span></span>

- [<span data-ttu-id="03107-122">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="03107-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="03107-123">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03107-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
