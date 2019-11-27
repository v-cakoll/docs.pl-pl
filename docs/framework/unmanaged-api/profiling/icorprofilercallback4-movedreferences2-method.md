---
title: ICorProfilerCallback4::MovedReferences2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 37d5f5e8294bb87a8796d6dcae046864904b096b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439372"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="bc663-102">ICorProfilerCallback4::MovedReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc663-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="bc663-103">Wywołuje się, by zgłosić nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bc663-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="bc663-104">Ta metoda jest wywoływana, jeśli Profiler zaimplementuje Interfejs [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bc663-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="bc663-105">To wywołanie zwrotne zastępuje metodę [ICorProfilerCallback:: MovedReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) , ponieważ umożliwia raportowanie większych zakresów obiektów, których długość przekracza, co może być wyrażone w ulong.</span><span class="sxs-lookup"><span data-stu-id="bc663-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc663-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc663-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc663-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc663-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="bc663-108">podczas Liczba bloków sąsiadujących obiektów, które zostały przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bc663-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="bc663-109">Oznacza to, że wartość `cMovedObjectIDRanges` jest łącznym rozmiarem `oldObjectIDRangeStart`, `newObjectIDRangeStart`i `cObjectIDRangeLength` tablic.</span><span class="sxs-lookup"><span data-stu-id="bc663-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="bc663-110">Kolejne trzy argumenty `MovedReferences2` są tablicami równoległymi.</span><span class="sxs-lookup"><span data-stu-id="bc663-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="bc663-111">Innymi słowy, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`i `cObjectIDRangeLength[i]` wszystkie dotyczą pojedynczego bloku ciągłych obiektów.</span><span class="sxs-lookup"><span data-stu-id="bc663-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="bc663-112">podczas Tablica wartości `ObjectID`, z których każdy jest starym (przed wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bc663-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="bc663-113">podczas Tablica wartości `ObjectID`, z których każdy jest nowym (wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bc663-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="bc663-114">podczas Tablica liczb całkowitych, z których każdy jest rozmiarem bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bc663-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="bc663-115">Rozmiar jest określony dla każdego bloku, do którego odwołuje się `oldObjectIDRangeStart` i `newObjectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="bc663-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc663-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc663-116">Remarks</span></span>  
 <span data-ttu-id="bc663-117">Kompaktowy moduł zbierający elementy bezużyteczne odzyskuje pamięć zajmowaną przez martwe obiekty i kompaktuje to wolne miejsce.</span><span class="sxs-lookup"><span data-stu-id="bc663-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="bc663-118">W związku z tym obiekty na żywo mogą być przenoszone w ramach sterty, a `ObjectID` wartości dystrybuowane przez poprzednie powiadomienia mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="bc663-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="bc663-119">Załóżmy, że istniejąca wartość `ObjectID` (`oldObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="bc663-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="bc663-120">W takim przypadku przesunięcie od początku zakresu do początku obiektu jest następujące:</span><span class="sxs-lookup"><span data-stu-id="bc663-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="bc663-121">Dla dowolnej wartości `i`, która znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="bc663-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="bc663-122">0 < = `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="bc663-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="bc663-123">nowe `ObjectID` można obliczyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bc663-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="bc663-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="bc663-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="bc663-125">Żadna z wartości `ObjectID` przesłanych przez `MovedReferences2` nie jest prawidłowa podczas wywołania zwrotnego, ponieważ moduł wyrzucania elementów bezużytecznych może być w trakcie przesuwania obiektów ze starych lokalizacji do nowych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="bc663-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="bc663-126">W związku z tym nie należy próbować kontrolować obiektów podczas wywołania `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="bc663-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="bc663-127">Wywołanie zwrotne [ICorProfilerCallback2:: GarbageCollectionFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcję.</span><span class="sxs-lookup"><span data-stu-id="bc663-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="bc663-128">Jeśli profiler implementuje zarówno interfejsy [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) , jak i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) , Metoda `MovedReferences2` jest wywoływana przed metodą [ICorProfilerCallback:: MovedReferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) , ale tylko wtedy, gdy metoda `MovedReferences2` zwróci się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bc663-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="bc663-129">Program do tworzenia plików może zwrócić wynik HRESULT wskazujący niepowodzenie z metody `MovedReferences2`, aby uniknąć wywoływania drugiej metody.</span><span class="sxs-lookup"><span data-stu-id="bc663-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc663-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc663-130">Requirements</span></span>  
 <span data-ttu-id="bc663-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc663-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc663-132">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bc663-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc663-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc663-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc663-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc663-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc663-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc663-135">See also</span></span>

- [<span data-ttu-id="bc663-136">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc663-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="bc663-137">MovedReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="bc663-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="bc663-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc663-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="bc663-139">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="bc663-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="bc663-140">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="bc663-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
