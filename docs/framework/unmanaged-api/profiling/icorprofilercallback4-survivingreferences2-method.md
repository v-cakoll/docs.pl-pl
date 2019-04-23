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
ms.openlocfilehash: ad96224daf79b17d3902217af061173580f1478a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122281"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="00b4a-102">ICorProfilerCallback4::SurvivingReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="00b4a-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="00b4a-103">Raportuje układ obiektów w stercie wyrzucania elementów bezużytecznych bez kondensowania w wyniku.</span><span class="sxs-lookup"><span data-stu-id="00b4a-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="00b4a-104">Ta metoda jest wywoływana, jeśli zaimplementowano program profilujący [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="00b4a-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="00b4a-105">Zastępuje to wywołanie zwrotne [icorprofilercallback2::survivingreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ponieważ może raportować większych zakresów obiektów, których długości przekracza, jakie mogą być wyrażone w ULONG.</span><span class="sxs-lookup"><span data-stu-id="00b4a-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00b4a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="00b4a-106">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="00b4a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="00b4a-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="00b4a-108">[in] Liczba bloków ciągłych obiektów, które przetrwały wyrzucanie elementów bezużytecznych bez kondensowania w wyniku.</span><span class="sxs-lookup"><span data-stu-id="00b4a-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="00b4a-109">Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które magazynu `ObjectID` i długość, odpowiednio dla każdego bloku obiektów.</span><span class="sxs-lookup"><span data-stu-id="00b4a-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="00b4a-110">Następne dwa argumenty `SurvivingReferences2` są tablicami równoległych.</span><span class="sxs-lookup"><span data-stu-id="00b4a-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="00b4a-111">Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłych obiektów.</span><span class="sxs-lookup"><span data-stu-id="00b4a-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="00b4a-112">[in] Tablica `ObjectID` wartości, z których każdy jest początkowy adres bloku ciągłych, obiekty aktywne w pamięci.</span><span class="sxs-lookup"><span data-stu-id="00b4a-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="00b4a-113">[in] Tablica liczb całkowitych, z których każdy jest rozmiar sprawny bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="00b4a-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="00b4a-114">Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `objectIDRangeStart` tablicy.</span><span class="sxs-lookup"><span data-stu-id="00b4a-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00b4a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00b4a-115">Remarks</span></span>  
 <span data-ttu-id="00b4a-116">Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablic powinien być interpretowany w następujący sposób w celu określenia, czy obiekt przetrwały wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="00b4a-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="00b4a-117">Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="00b4a-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="00b4a-118">Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma przetrwały wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="00b4a-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="00b4a-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="00b4a-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="00b4a-120">Wyrzucanie elementów bezużytecznych bez kondensowania odzyskuje pamięć zajęta przez obiekty "martwe", ale nie compact zwolnione miejsca.</span><span class="sxs-lookup"><span data-stu-id="00b4a-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="00b4a-121">W rezultacie pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="00b4a-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="00b4a-122">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences2` dla bez kondensowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="00b4a-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="00b4a-123">Do kompaktowania wyrzucania elementów bezużytecznych [movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) zamiast tego wywoływany jest.</span><span class="sxs-lookup"><span data-stu-id="00b4a-123">For compacting garbage collections, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="00b4a-124">Pojedynczy wyrzucania elementów bezużytecznych może być kompaktowania jeden generacji i bez kondensowania dla innego.</span><span class="sxs-lookup"><span data-stu-id="00b4a-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="00b4a-125">Wyrzucanie elementów bezużytecznych na dowolnym konkretnej generacji, program profilujący wyświetlany żaden `SurvivingReferences2` wywołanie zwrotne lub [movedreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) wywołania zwrotnego, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="00b4a-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="00b4a-126">Wiele `SurvivingReferences2` wywołania zwrotne może być odbierane podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone wewnętrznego buforowania, wiele wywołań zwrotnych podczas wyrzucania elementów bezużytecznych dla serwera i innych powodów.</span><span class="sxs-lookup"><span data-stu-id="00b4a-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="00b4a-127">W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacje są zbiorcze; wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences2` wywołania zwrotnego przetrwać wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="00b4a-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="00b4a-128">Gdy profiler implementuje zarówno [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsów, `SurvivingReferences2` metoda jest wywoływana przed [ICorProfilerCallback2:: Survivingreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ale tylko wtedy, gdy `SurvivingReferences2` wróci pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="00b4a-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="00b4a-129">Profilery może zwrócić HRESULT, która wskazuje błędu na podstawie `SurvivingReferences2` metodę, aby uniknąć wywoływania drugiej metody.</span><span class="sxs-lookup"><span data-stu-id="00b4a-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00b4a-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00b4a-130">Requirements</span></span>  
 <span data-ttu-id="00b4a-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00b4a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00b4a-132">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00b4a-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00b4a-133">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00b4a-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00b4a-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00b4a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b4a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00b4a-135">See also</span></span>

- [<span data-ttu-id="00b4a-136">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="00b4a-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="00b4a-137">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="00b4a-137">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="00b4a-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="00b4a-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
