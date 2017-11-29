---
title: "ICorProfilerCallback2::SurvivingReferences — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.SurvivingReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3764bfb79b39af897600202e8bc0f2ffbc4da95b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="75559-102">ICorProfilerCallback2::SurvivingReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="75559-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="75559-103">Raporty układ obiektów na stercie wyniku-kompaktowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75559-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75559-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75559-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75559-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75559-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="75559-106">[in] Liczba bloków ciągłe obiektów, które udało przetrwać wyniku-kompaktowania wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75559-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="75559-107">Oznacza to, że wartość `cSurvivingObjectIDRanges` rozmiar `objectIDRangeStart` i `cObjectIDRangeLength` stałych, w których magazyn `ObjectID` oraz długość, odpowiednio do każdego bloku obiektów.</span><span class="sxs-lookup"><span data-stu-id="75559-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="75559-108">Następne dwa argumenty `SurvivingReferences` tablice równoległych.</span><span class="sxs-lookup"><span data-stu-id="75559-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="75559-109">Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłe obiektów.</span><span class="sxs-lookup"><span data-stu-id="75559-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="75559-110">[in] Tablica `ObjectID` wartości, z których każdy jest adres początkowy blok ciągłym, live obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="75559-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="75559-111">[in] Tablica liczb całkowitych, z których każdy jest rozmiar bloku sprawny ciągłe obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="75559-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="75559-112">Rozmiar jest określony dla każdego bloku, który odwołuje się do `objectIDRangeStart` tablicy.</span><span class="sxs-lookup"><span data-stu-id="75559-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75559-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75559-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75559-114">Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="75559-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="75559-115">Dla obiektów, które są większe niż 4 GB, użyj [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="75559-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="75559-116">Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być rozumiane w następujący sposób, aby określić, czy udało się obiektu przetrwać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75559-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="75559-117">Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="75559-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="75559-118">Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma udało przetrwać wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="75559-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="75559-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="75559-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="75559-120">Kompaktowania wyrzucania elementów bezużytecznych zwraca pamięci zajmowany przez obiekty "martwy", ale nie compact zwolnionych miejsca.</span><span class="sxs-lookup"><span data-stu-id="75559-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="75559-121">W związku z tym pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="75559-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="75559-122">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences` dla-kompaktowania wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75559-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="75559-123">Kolekcje garbage kompaktowania [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) jest wywoływana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="75559-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="75559-124">Pojedynczy wyrzucania elementów bezużytecznych można kompaktowania jeden generacji i z systemem innym niż kompaktowania dla innej.</span><span class="sxs-lookup"><span data-stu-id="75559-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="75559-125">Wyrzucanie elementów bezużytecznych na dowolnym określonym generacji profilera wyświetlany żaden `SurvivingReferences` wywołania zwrotnego lub `MovedReferences` wywołania zwrotnego, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="75559-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="75559-126">Wiele `SurvivingReferences` wywołania zwrotne może otrzymał podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone buforowania wewnętrznego, wiele wątków raportowania w przypadku odzyskiwanie pamięci na serwerze i innych powodów.</span><span class="sxs-lookup"><span data-stu-id="75559-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="75559-127">W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych, informacje są zbiorcza — wszystkich odwołań, które są zgłaszane w żadnym `SurvivingReferences` wywołania zwrotnego przetrwać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75559-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75559-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75559-128">Requirements</span></span>  
 <span data-ttu-id="75559-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75559-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75559-130">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75559-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75559-131">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75559-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75559-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75559-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75559-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75559-133">See Also</span></span>  
 [<span data-ttu-id="75559-134">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="75559-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="75559-135">ICorProfilerCallback2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="75559-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="75559-136">SurvivingReferences2 — metoda</span><span class="sxs-lookup"><span data-stu-id="75559-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
