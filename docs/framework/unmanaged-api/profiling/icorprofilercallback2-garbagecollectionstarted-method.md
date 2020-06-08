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
ms.openlocfilehash: f025f4c0bc0ec8e11decddcdf64be50f68955266
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499808"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="6af52-102">ICorProfilerCallback2::GarbageCollectionStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="6af52-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="6af52-103">Powiadamia profiler kodu o rozpoczęciu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="6af52-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6af52-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6af52-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="6af52-106">podczas Łączna liczba wpisów w `generationCollected` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6af52-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="6af52-107">podczas Tablica wartości logicznych, które są, `true` Jeśli generacja, która odpowiada indeksowi tablicy jest zbierana przez to wyrzucanie elementów bezużytecznych; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="6af52-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="6af52-108">Tablica jest indeksowana przez wartość wyliczenia [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , która wskazuje generowanie.</span><span class="sxs-lookup"><span data-stu-id="6af52-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="6af52-109">podczas Wartość wyliczenia [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) , która wskazuje przyczynę wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6af52-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6af52-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6af52-110">Remarks</span></span>  
 <span data-ttu-id="6af52-111">Wszystkie wywołania zwrotne, które odnoszą się do tego wyrzucania elementów bezużytecznych, następują między `GarbageCollectionStarted` wywołaniem zwrotnym a odpowiednim wywołaniem zwrotnym [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="6af52-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="6af52-112">Te wywołania zwrotne nie muszą występować w tym samym wątku.</span><span class="sxs-lookup"><span data-stu-id="6af52-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="6af52-113">Program profilujący może bezpiecznie zbadać obiekty w ich oryginalnych lokalizacjach podczas `GarbageCollectionStarted` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6af52-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="6af52-114">Moduł wyrzucania elementów bezużytecznych rozpocznie przesuwanie obiektów po zwrocie z `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="6af52-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="6af52-115">Po zwróceniu przez profiler z tego wywołania zwrotnego, profiler powinien wziąć pod uwagę wszystkie identyfikatory obiektów, które mają być nieprawidłowe do momentu odebrania `ICorProfilerCallback2::GarbageCollectionFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6af52-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af52-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6af52-116">Requirements</span></span>  
 <span data-ttu-id="6af52-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6af52-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af52-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6af52-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6af52-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6af52-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6af52-120">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af52-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af52-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6af52-121">See also</span></span>

- [<span data-ttu-id="6af52-122">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6af52-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6af52-123">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6af52-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
