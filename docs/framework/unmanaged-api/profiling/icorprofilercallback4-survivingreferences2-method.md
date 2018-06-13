---
title: ICorProfilerCallback4::SurvivingReferences2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de081286096a9001ff48b565baeb47a1d1a4f28a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460349"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="e12fa-102">ICorProfilerCallback4::SurvivingReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="e12fa-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="e12fa-103">Raporty układ obiektów na stercie wyniku-kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e12fa-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="e12fa-104">Ta metoda jest wywoływana, jeśli zaimplementowano profilera [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e12fa-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="e12fa-105">To wywołanie zwrotne zastępuje [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, którego długość przekracza może zostać wyrażona w ULONG.</span><span class="sxs-lookup"><span data-stu-id="e12fa-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e12fa-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e12fa-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e12fa-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e12fa-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="e12fa-108">[in] Liczba bloków ciągłe obiektów, które udało przetrwać wyniku-kompaktowania wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e12fa-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="e12fa-109">Oznacza to, że wartość `cSurvivingObjectIDRanges` rozmiar `objectIDRangeStart` i `cObjectIDRangeLength` stałych, w których magazyn `ObjectID` oraz długość, odpowiednio do każdego bloku obiektów.</span><span class="sxs-lookup"><span data-stu-id="e12fa-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="e12fa-110">Następne dwa argumenty `SurvivingReferences2` tablice równoległych.</span><span class="sxs-lookup"><span data-stu-id="e12fa-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="e12fa-111">Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłe obiektów.</span><span class="sxs-lookup"><span data-stu-id="e12fa-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="e12fa-112">[in] Tablica `ObjectID` wartości, z których każdy jest adres początkowy blok ciągłym, live obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e12fa-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="e12fa-113">[in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku sprawny ciągłe obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e12fa-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="e12fa-114">Rozmiar jest określony dla każdego bloku, który odwołuje się do `objectIDRangeStart` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e12fa-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e12fa-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e12fa-115">Remarks</span></span>  
 <span data-ttu-id="e12fa-116">Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być rozumiane w następujący sposób, aby określić, czy udało się obiektu przetrwać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e12fa-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="e12fa-117">Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="e12fa-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="e12fa-118">Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma udało przetrwać wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="e12fa-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="e12fa-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="e12fa-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="e12fa-120">Kompaktowania wyrzucania elementów bezużytecznych zwraca pamięci zajmowany przez obiekty "martwy", ale nie compact zwolnionych miejsca.</span><span class="sxs-lookup"><span data-stu-id="e12fa-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="e12fa-121">W związku z tym pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="e12fa-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="e12fa-122">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences2` dla-kompaktowania wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e12fa-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="e12fa-123">Kolekcje garbage kompaktowania [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) jest wywoływana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e12fa-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="e12fa-124">Pojedynczy wyrzucania elementów bezużytecznych można kompaktowania jeden generacji i z systemem innym niż kompaktowania dla innej.</span><span class="sxs-lookup"><span data-stu-id="e12fa-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="e12fa-125">Wyrzucanie elementów bezużytecznych na dowolnym określonym generacji profilera wyświetlany żaden `SurvivingReferences2` wywołania zwrotnego lub [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) wywołania zwrotnego, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="e12fa-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="e12fa-126">Wiele `SurvivingReferences2` wywołania zwrotne może odbierane podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone buforowanie wewnętrznego, wielu wywołań zwrotnych podczas odzyskiwanie pamięci na serwerze i innych powodów.</span><span class="sxs-lookup"><span data-stu-id="e12fa-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="e12fa-127">W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacje są zbiorczą; wszystkie odwołania zgłaszanych w żadnym `SurvivingReferences2` wywołania zwrotnego przetrwać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e12fa-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="e12fa-128">Jeśli profilera implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `SurvivingReferences2` metoda jest wywoływana przed [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ale tylko wtedy, gdy `SurvivingReferences2` zwraca pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e12fa-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="e12fa-129">Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `SurvivingReferences2` metody w celu uniknięcia wywołanie metody drugiego.</span><span class="sxs-lookup"><span data-stu-id="e12fa-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e12fa-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e12fa-130">Requirements</span></span>  
 <span data-ttu-id="e12fa-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e12fa-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e12fa-132">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e12fa-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e12fa-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e12fa-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e12fa-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e12fa-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12fa-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e12fa-135">See Also</span></span>  
 [<span data-ttu-id="e12fa-136">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e12fa-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e12fa-137">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e12fa-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="e12fa-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="e12fa-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
