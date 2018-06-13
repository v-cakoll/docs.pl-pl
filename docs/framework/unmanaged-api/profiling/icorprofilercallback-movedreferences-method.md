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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28fa18535cce50a62f6aca7ae6f013628698c6dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455538"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="ee32f-102">ICorProfilerCallback::MovedReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="ee32f-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="ee32f-103">Wywołuje się, by raportu nowy układ obiektów na stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ee32f-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee32f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee32f-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee32f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee32f-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="ee32f-106">[in] Liczba bloków ciągłe obiektów, które przeniesiona w wyniku kompaktowania wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ee32f-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="ee32f-107">Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.</span><span class="sxs-lookup"><span data-stu-id="ee32f-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="ee32f-108">Argumenty trzech kolejnych `MovedReferences` tablice równoległych.</span><span class="sxs-lookup"><span data-stu-id="ee32f-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="ee32f-109">Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłe obiektów.</span><span class="sxs-lookup"><span data-stu-id="ee32f-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="ee32f-110">[in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucanie elementów bezużytecznych) początkowy adres bloku ciągłym, live obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ee32f-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="ee32f-111">[in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucanie elementów bezużytecznych) bloku ciągłym, live obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ee32f-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="ee32f-112">[in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłe obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ee32f-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="ee32f-113">Rozmiar jest określony dla każdego bloku, który odwołuje się do `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.</span><span class="sxs-lookup"><span data-stu-id="ee32f-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee32f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee32f-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee32f-115">Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="ee32f-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="ee32f-116">Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, należy użyć [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ee32f-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="ee32f-117">Kompaktowanie modułu zbierającego elementy bezużyteczne zwraca pamięci zajmowany przez obiekty martwy i kompaktuje, które zwolnienie miejsca.</span><span class="sxs-lookup"><span data-stu-id="ee32f-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="ee32f-118">W związku z tym na żywo obiekty mogą być przeniesione w stercie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ee32f-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="ee32f-119">Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="ee32f-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="ee32f-120">W takim przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ee32f-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="ee32f-121">Dla dowolnej wartości `i` znajdujący się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="ee32f-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="ee32f-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="ee32f-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="ee32f-123">można obliczyć nowego `ObjectID` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ee32f-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="ee32f-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="ee32f-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="ee32f-125">Żadna z `ObjectID` wartości przekazywane przez `MovedReferences` obowiązują podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów z starego lokalizacji do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="ee32f-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="ee32f-126">W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `MovedReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="ee32f-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="ee32f-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do nowej lokalizacji i inspekcji mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="ee32f-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee32f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee32f-128">Requirements</span></span>  
 <span data-ttu-id="ee32f-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee32f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee32f-130">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee32f-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee32f-131">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee32f-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee32f-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee32f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee32f-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee32f-133">See Also</span></span>  
 [<span data-ttu-id="ee32f-134">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee32f-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ee32f-135">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="ee32f-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [<span data-ttu-id="ee32f-136">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ee32f-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ee32f-137">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="ee32f-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
