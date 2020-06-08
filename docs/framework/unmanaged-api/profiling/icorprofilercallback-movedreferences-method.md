---
title: ICorProfilerCallback::MovedReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503342"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="d3460-102">ICorProfilerCallback::MovedReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3460-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="d3460-103">Wywołuje się, by zgłosić nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d3460-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3460-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3460-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3460-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3460-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="d3460-106">podczas Liczba bloków sąsiadujących obiektów, które zostały przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d3460-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="d3460-107">Oznacza to, że wartość `cMovedObjectIDRanges` jest łącznym rozmiarem `oldObjectIDRangeStart` `newObjectIDRangeStart` tablic,, i `cObjectIDRangeLength` .</span><span class="sxs-lookup"><span data-stu-id="d3460-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="d3460-108">Następne trzy argumenty `MovedReferences` są równoległymi tablicami.</span><span class="sxs-lookup"><span data-stu-id="d3460-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="d3460-109">Innymi słowy,, `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]` i `cObjectIDRangeLength[i]` wszystkie dotyczą pojedynczego bloku ciągłego obiektów.</span><span class="sxs-lookup"><span data-stu-id="d3460-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="d3460-110">podczas Tablica `ObjectID` wartości, z których każdy jest starym (przed wyrzucaniem elementów bezużytecznych) adres początkowy bloku ciągłego, na żywo obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d3460-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="d3460-111">podczas Tablica `ObjectID` wartości, z których każdy jest nowym (wyrzucanym po sobie) adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d3460-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="d3460-112">podczas Tablica liczb całkowitych, z których każdy jest rozmiarem bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d3460-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="d3460-113">Rozmiar jest określony dla każdego bloku, do którego odwołuje się `oldObjectIDRangeStart` `newObjectIDRangeStart` Tablica i.</span><span class="sxs-lookup"><span data-stu-id="d3460-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3460-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3460-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3460-115">Ta metoda zgłasza rozmiary `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="d3460-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="d3460-116">Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, należy zamiast tego użyć metody [ICorProfilerCallback4:: MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d3460-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="d3460-117">Kompaktowy moduł zbierający elementy bezużyteczne odzyskuje pamięć zajmowaną przez martwe obiekty i kompaktuje to wolne miejsce.</span><span class="sxs-lookup"><span data-stu-id="d3460-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="d3460-118">W związku z tym obiekty na żywo mogą być przenoszone w ramach sterty, a `ObjectID` wartości dystrybuowane przez poprzednie powiadomienia mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="d3460-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="d3460-119">Załóżmy, że istniejąca `ObjectID` wartość ( `oldObjectID` ) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="d3460-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="d3460-120">W takim przypadku przesunięcie od początku zakresu do początku obiektu jest następujące:</span><span class="sxs-lookup"><span data-stu-id="d3460-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="d3460-121">Dla dowolnej wartości `i` , która znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="d3460-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="d3460-122">0 <=`i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="d3460-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="d3460-123">nowe wartości można obliczyć `ObjectID` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d3460-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="d3460-124">`newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )</span><span class="sxs-lookup"><span data-stu-id="d3460-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="d3460-125">Żadna z `ObjectID` wartości przesłanych przez nie `MovedReferences` jest prawidłowa podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych lokalizacji do nowych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d3460-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="d3460-126">W związku z tym nie należy próbować kontrolować obiektów podczas `MovedReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="d3460-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="d3460-127">Wywołanie zwrotne [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i można przeprowadzić inspekcję.</span><span class="sxs-lookup"><span data-stu-id="d3460-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3460-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3460-128">Requirements</span></span>  
 <span data-ttu-id="d3460-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3460-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3460-130">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d3460-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3460-131">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d3460-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3460-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3460-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3460-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3460-133">See also</span></span>

- [<span data-ttu-id="d3460-134">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3460-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d3460-135">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="d3460-135">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="d3460-136">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="d3460-136">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d3460-137">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="d3460-137">Profiling</span></span>](index.md)
