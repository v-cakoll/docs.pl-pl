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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d368c88503853d0620f28f02f88a6d887c1aa681
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156406"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="cd709-102">ICorProfilerCallback4::MovedReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd709-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="cd709-103">Wywołuje się, aby zgłosić nowy układ obiektów w stercie wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cd709-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="cd709-104">Ta metoda jest wywoływana, jeśli zaimplementowano program profilujący [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cd709-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="cd709-105">Zastępuje to wywołanie zwrotne [icorprofilercallback::movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, których długości przekracza, jakie mogą być wyrażone w ULONG.</span><span class="sxs-lookup"><span data-stu-id="cd709-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd709-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd709-106">Syntax</span></span>  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd709-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd709-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="cd709-108">[in] Liczba bloków ciągłych obiektów, które przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cd709-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="cd709-109">Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.</span><span class="sxs-lookup"><span data-stu-id="cd709-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="cd709-110">Następne trzy argumenty `MovedReferences2` są tablicami równoległych.</span><span class="sxs-lookup"><span data-stu-id="cd709-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="cd709-111">Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłych obiektów.</span><span class="sxs-lookup"><span data-stu-id="cd709-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="cd709-112">[in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucania elementów bezużytecznych) początkowy adres bloku ciągłych, obiekty aktywne w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd709-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="cd709-113">[in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucania elementów bezużytecznych), bloku ciągłych, obiekty aktywne w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd709-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="cd709-114">[in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd709-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="cd709-115">Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.</span><span class="sxs-lookup"><span data-stu-id="cd709-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd709-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd709-116">Remarks</span></span>  
 <span data-ttu-id="cd709-117">Kompaktowania moduł odśmiecania pamięci odzyskuje pamięć zajęta przez obiekty martwe i kompaktuje, które zwolnienie miejsca.</span><span class="sxs-lookup"><span data-stu-id="cd709-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="cd709-118">W rezultacie obiekty na żywo mogą być przeniesione w stosie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="cd709-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="cd709-119">Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="cd709-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="cd709-120">W tym przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="cd709-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="cd709-121">Dla dowolnej wartości `i` znajdujący się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="cd709-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="cd709-122">0 <= `i` < </span><span class="sxs-lookup"><span data-stu-id="cd709-122">0 <= `i` < </span></span>`cMovedObjectIDRanges`  
  
 <span data-ttu-id="cd709-123">można obliczyć nową `ObjectID` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cd709-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 `newObjectID`<span data-ttu-id="cd709-124"> = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]\`)</span><span class="sxs-lookup"><span data-stu-id="cd709-124"> = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]\`)</span></span>  
  
 <span data-ttu-id="cd709-125">Żaden z `ObjectID` wartości przekazanych przez `MovedReferences2` obowiązują podczas wywołania zwrotnego, ponieważ moduł odśmiecania pamięci może być w trakcie przenoszenia obiektów z lokalizacji starej do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cd709-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="cd709-126">W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `MovedReferences2` wywołania.</span><span class="sxs-lookup"><span data-stu-id="cd709-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="cd709-127">A [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i inspekcji mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="cd709-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="cd709-128">Gdy profiler implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `MovedReferences2` metoda jest wywoływana przed [ICorProfilerCallback:: Movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metody, ale tylko wtedy, gdy `MovedReferences2` metoda zwraca pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cd709-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="cd709-129">Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `MovedReferences2` metody, aby uniknąć wywoływania drugiej metody.</span><span class="sxs-lookup"><span data-stu-id="cd709-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd709-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd709-130">Requirements</span></span>  
 <span data-ttu-id="cd709-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd709-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd709-132">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd709-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd709-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd709-133">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cd709-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cd709-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd709-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd709-135">See also</span></span>

- [<span data-ttu-id="cd709-136">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd709-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cd709-137">MovedReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="cd709-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="cd709-138">ICorProfilerCallback4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd709-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="cd709-139">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cd709-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="cd709-140">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="cd709-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
