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
ms.openlocfilehash: c90c790c519cc0c422657e6e2d8040a365fbf48c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865782"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="82ff3-102">ICorProfilerCallback2::GarbageCollectionStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="82ff3-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="82ff3-103">Powiadamia profiler kodu o rozpoczęciu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="82ff3-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ff3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82ff3-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82ff3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82ff3-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="82ff3-106">podczas Łączna liczba wpisów w tablicy `generationCollected`.</span><span class="sxs-lookup"><span data-stu-id="82ff3-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="82ff3-107">podczas Tablica wartości logicznych, które są `true`, jeśli generacja, która odpowiada indeksowi tablicy jest zbierana przez to wyrzucanie elementów bezużytecznych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="82ff3-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="82ff3-108">Tablica jest indeksowana przez wartość wyliczenia [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , która wskazuje generowanie.</span><span class="sxs-lookup"><span data-stu-id="82ff3-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="82ff3-109">podczas Wartość wyliczenia [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) , która wskazuje przyczynę wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82ff3-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82ff3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82ff3-110">Remarks</span></span>  
 <span data-ttu-id="82ff3-111">Wszystkie wywołania zwrotne, które odnoszą się do tego wyrzucania elementów bezużytecznych, następują między wywołaniem zwrotnym `GarbageCollectionStarted` i odpowiednim wywołaniem zwrotnym [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="82ff3-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="82ff3-112">Te wywołania zwrotne nie muszą występować w tym samym wątku.</span><span class="sxs-lookup"><span data-stu-id="82ff3-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="82ff3-113">Program profilujący może bezpiecznie zbadać obiekty w ich oryginalnych lokalizacjach podczas wywołania zwrotnego `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="82ff3-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="82ff3-114">Moduł wyrzucania elementów bezużytecznych rozpocznie przesuwanie obiektów po powrocie z `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="82ff3-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="82ff3-115">Po zwróceniu przez profiler z tego wywołania zwrotnego, profiler powinien wziąć pod uwagę wszystkie identyfikatory obiektów, które mają być nieprawidłowe do momentu odebrania wywołania zwrotnego `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="82ff3-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82ff3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82ff3-116">Requirements</span></span>  
 <span data-ttu-id="82ff3-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82ff3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82ff3-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="82ff3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82ff3-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82ff3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82ff3-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82ff3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ff3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82ff3-121">See also</span></span>

- [<span data-ttu-id="82ff3-122">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="82ff3-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="82ff3-123">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="82ff3-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
