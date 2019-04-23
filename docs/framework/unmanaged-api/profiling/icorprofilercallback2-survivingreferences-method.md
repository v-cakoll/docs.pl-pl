---
title: ICorProfilerCallback2::SurvivingReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191305"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="a69c7-102">ICorProfilerCallback2::SurvivingReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="a69c7-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="a69c7-103">Raportuje układ obiektów w stercie wyrzucania elementów bezużytecznych bez kondensowania w wyniku.</span><span class="sxs-lookup"><span data-stu-id="a69c7-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a69c7-104">Syntax</span></span>  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a69c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a69c7-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="a69c7-106">[in] Liczba bloków ciągłych obiektów, które przetrwały wyrzucanie elementów bezużytecznych bez kondensowania w wyniku.</span><span class="sxs-lookup"><span data-stu-id="a69c7-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="a69c7-107">Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które magazynu `ObjectID` i długość, odpowiednio dla każdego bloku obiektów.</span><span class="sxs-lookup"><span data-stu-id="a69c7-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="a69c7-108">Następne dwa argumenty `SurvivingReferences` są tablicami równoległych.</span><span class="sxs-lookup"><span data-stu-id="a69c7-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="a69c7-109">Innymi słowy `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a69c7-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="a69c7-110">[in] Tablica `ObjectID` wartości, z których każdy jest początkowy adres bloku ciągłych, obiekty aktywne w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a69c7-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="a69c7-111">[in] Tablica liczb całkowitych, z których każdy jest rozmiar sprawny bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a69c7-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="a69c7-112">Rozmiar jest określony dla każdego bloku, w której podano odwołanie w `objectIDRangeStart` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a69c7-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a69c7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a69c7-113">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a69c7-114">Ta metoda zgłasza rozmiary jako `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="a69c7-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="a69c7-115">W przypadku obiektów, które są większe niż 4 GB, użyj [icorprofilercallback4::survivingreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a69c7-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="a69c7-116">Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablic powinien być interpretowany w następujący sposób w celu określenia, czy obiekt przetrwały wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a69c7-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="a69c7-117">Przyjęto założenie, że `ObjectID` wartość (`ObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="a69c7-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="a69c7-118">Dla dowolnej wartości `i` znajdujący się w następującym zakresie, obiekt ma przetrwały wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="a69c7-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="a69c7-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="a69c7-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="a69c7-120">Wyrzucanie elementów bezużytecznych bez kondensowania odzyskuje pamięć zajęta przez obiekty "martwe", ale nie compact zwolnione miejsca.</span><span class="sxs-lookup"><span data-stu-id="a69c7-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="a69c7-121">W rezultacie pamięci jest zwracany do sterty, ale żadne obiekty "na żywo" są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="a69c7-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="a69c7-122">Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `SurvivingReferences` dla bez kondensowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a69c7-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="a69c7-123">Do kompaktowania wyrzucania elementów bezużytecznych [icorprofilercallback::movedreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) zamiast tego wywoływany jest.</span><span class="sxs-lookup"><span data-stu-id="a69c7-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="a69c7-124">Pojedynczy wyrzucania elementów bezużytecznych może być kompaktowania jeden generacji i bez kondensowania dla innego.</span><span class="sxs-lookup"><span data-stu-id="a69c7-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="a69c7-125">Wyrzucanie elementów bezużytecznych na dowolnym konkretnej generacji, program profilujący wyświetlany żaden `SurvivingReferences` wywołanie zwrotne lub `MovedReferences` wywołania zwrotnego, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="a69c7-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="a69c7-126">Wiele `SurvivingReferences` wywołań zwrotnych mogą odebranych podczas określonego wyrzucania elementów bezużytecznych, ze względu na ograniczone wewnętrznego buforowania, wiele wątków raportowania w przypadku serwer wyrzucania elementów bezużytecznych i innych powodów.</span><span class="sxs-lookup"><span data-stu-id="a69c7-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="a69c7-127">W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych, informacje są zbiorczej — wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences` wywołania zwrotnego przetrwać wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a69c7-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69c7-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a69c7-128">Requirements</span></span>  
 <span data-ttu-id="a69c7-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a69c7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a69c7-130">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a69c7-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a69c7-131">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a69c7-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a69c7-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a69c7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69c7-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a69c7-133">See also</span></span>

- [<span data-ttu-id="a69c7-134">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a69c7-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a69c7-135">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a69c7-135">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="a69c7-136">SurvivingReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="a69c7-136">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
