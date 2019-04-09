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
ms.openlocfilehash: 4611b8c186e0293dae73cee4f9d845bb44c167c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073549"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="50dd4-102">ICorProfilerCallback::MovedReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="50dd4-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="50dd4-103">Wywołuje się, aby zgłosić nowy układ obiektów w stercie wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="50dd4-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50dd4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50dd4-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="50dd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50dd4-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="50dd4-106">[in] Liczba bloków ciągłych obiektów, które przeniesione w wyniku kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="50dd4-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="50dd4-107">Oznacza to, że wartość `cMovedObjectIDRanges` jest całkowity rozmiar `oldObjectIDRangeStart`, `newObjectIDRangeStart`, i `cObjectIDRangeLength` tablic.</span><span class="sxs-lookup"><span data-stu-id="50dd4-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="50dd4-108">Następne trzy argumenty `MovedReferences` są tablicami równoległych.</span><span class="sxs-lookup"><span data-stu-id="50dd4-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="50dd4-109">Innymi słowy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, i `cObjectIDRangeLength[i]` dotyczą wszystkich jeden blok ciągłych obiektów.</span><span class="sxs-lookup"><span data-stu-id="50dd4-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="50dd4-110">[in] Tablica `ObjectID` wartości, z których każdy jest stary (wstępne wyrzucania elementów bezużytecznych) początkowy adres bloku ciągłych, obiekty aktywne w pamięci.</span><span class="sxs-lookup"><span data-stu-id="50dd4-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="50dd4-111">[in] Tablica `ObjectID` wartości, z których każdy jest nowy adres początkowy (po wyrzucania elementów bezużytecznych), bloku ciągłych, obiekty aktywne w pamięci.</span><span class="sxs-lookup"><span data-stu-id="50dd4-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="50dd4-112">[in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="50dd4-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="50dd4-113">Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `oldObjectIDRangeStart` i `newObjectIDRangeStart` tablic.</span><span class="sxs-lookup"><span data-stu-id="50dd4-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50dd4-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50dd4-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50dd4-115">Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="50dd4-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="50dd4-116">Aby uzyskać rozmiar obiektów, które są większe niż 4 GB, użyj [icorprofilercallback4::movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="50dd4-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="50dd4-117">Kompaktowania moduł odśmiecania pamięci odzyskuje pamięć zajęta przez obiekty martwe i kompaktuje, które zwolnienie miejsca.</span><span class="sxs-lookup"><span data-stu-id="50dd4-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="50dd4-118">W rezultacie obiekty na żywo mogą być przeniesione w stosie, i `ObjectID` wartości rozdzielonych powiadomienia mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="50dd4-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="50dd4-119">Przyjęto założenie, że istniejące `ObjectID` wartość (`oldObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="50dd4-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="50dd4-120">W tym przypadku przesunięcie od początku zakresu do rozpoczęcia obiektu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="50dd4-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="50dd4-121">Dla dowolnej wartości `i` znajdujący się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="50dd4-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="50dd4-122">0 <= `i` < </span><span class="sxs-lookup"><span data-stu-id="50dd4-122">0 <= `i` < </span></span>`cMovedObjectIDRanges`  
  
 <span data-ttu-id="50dd4-123">można obliczyć nową `ObjectID` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="50dd4-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 `newObjectID`<span data-ttu-id="50dd4-124"> = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]\`)</span><span class="sxs-lookup"><span data-stu-id="50dd4-124"> = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]\`)</span></span>  
  
 <span data-ttu-id="50dd4-125">Żaden z `ObjectID` wartości przekazanych przez `MovedReferences` obowiązują podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów z lokalizacji starej do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="50dd4-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="50dd4-126">W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `MovedReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="50dd4-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="50dd4-127">A [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) wywołania zwrotnego wskazuje, że wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i inspekcji mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="50dd4-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50dd4-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50dd4-128">Requirements</span></span>  
 <span data-ttu-id="50dd4-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50dd4-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50dd4-130">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50dd4-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50dd4-131">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50dd4-131">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="50dd4-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="50dd4-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50dd4-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50dd4-133">See also</span></span>

- [<span data-ttu-id="50dd4-134">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="50dd4-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="50dd4-135">MovedReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="50dd4-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="50dd4-136">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="50dd4-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="50dd4-137">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="50dd4-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
