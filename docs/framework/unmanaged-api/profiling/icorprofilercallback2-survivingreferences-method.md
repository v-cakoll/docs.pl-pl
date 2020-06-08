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
ms.openlocfilehash: 3681106bca94f1fefb2f24a1aa4254eb2b1b0531
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499743"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="c6e0e-102">ICorProfilerCallback2::SurvivingReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6e0e-102">ICorProfilerCallback2::SurvivingReferences Method</span></span>
<span data-ttu-id="c6e0e-103">Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e0e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6e0e-104">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6e0e-105">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="c6e0e-106">podczas Liczba bloków ciągłych obiektów, które przeżyły jako wynik niekompaktowego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-106">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="c6e0e-107">Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` `cObjectIDRangeLength` tablic i, które przechowują `ObjectID` odpowiednio długość i dla każdego bloku obiektów.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-107">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="c6e0e-108">Dwa następne argumenty `SurvivingReferences` są równoległymi tablicami.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-108">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="c6e0e-109">Innymi słowy `objectIDRangeStart` i dotyczy tego `cObjectIDRangeLength` samego bloku sąsiadujących obiektów.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-109">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="c6e0e-110">podczas Tablica `ObjectID` wartości, z których każdy jest adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-110">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="c6e0e-111">podczas Tablica liczb całkowitych, z których każdy jest rozmiarem ciągłego bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-111">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="c6e0e-112">Dla każdego bloku, do którego odwołuje się tablica, jest określony rozmiar `objectIDRangeStart` .</span><span class="sxs-lookup"><span data-stu-id="c6e0e-112">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6e0e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6e0e-113">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c6e0e-114">Ta metoda zgłasza rozmiary `MAX_ULONG` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-114">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="c6e0e-115">W przypadku obiektów, które są większe niż 4 GB, zamiast tego użyj metody [ICorProfilerCallback4:: SurvivingReferences2 —](icorprofilercallback4-survivingreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6e0e-115">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="c6e0e-116">Elementy `objectIDRangeStart` `cObjectIDRangeLength` tablic i powinny być interpretowane w następujący sposób, aby określić, czy obiekt przeżyje odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="c6e0e-117">Załóżmy, że `ObjectID` wartość ( `ObjectID` ) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="c6e0e-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="c6e0e-118">Dla każdej wartości `i` , która znajduje się w następującym zakresie, obiekt przeżyły odzyskiwanie pamięci:</span><span class="sxs-lookup"><span data-stu-id="c6e0e-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="c6e0e-119">0 <=`i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="c6e0e-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="c6e0e-120">Niekompaktowe wyrzucanie elementów bezużytecznych przejmuje pamięć zajmowaną przez obiekty "martwe", ale nie kompaktuje ilości wolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="c6e0e-121">W efekcie do sterty jest zwracana pamięć, ale nie są przenoszone żadne obiekty "na żywo".</span><span class="sxs-lookup"><span data-stu-id="c6e0e-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="c6e0e-122">Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `SurvivingReferences` dla niekompaktowych kolekcji elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-122">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="c6e0e-123">W przypadku kompaktowania kolekcji elementów bezużytecznych zamiast niej wywoływana jest [ICorProfilerCallback:: MovedReferences —](icorprofilercallback-movedreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6e0e-123">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="c6e0e-124">Pojedyncze wyrzucanie elementów bezużytecznych może być kompaktowania dla jednej generacji i niekompaktowania dla innych.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="c6e0e-125">W przypadku wyrzucania elementów bezużytecznych na określonej generacji Profiler otrzyma `SurvivingReferences` wywołanie zwrotne lub `MovedReferences` wywołanie zwrotne, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="c6e0e-126">`SurvivingReferences`Podczas konkretnego wyrzucania elementów bezużytecznych może zostać odebranych wiele wywołań zwrotnych z powodu ograniczonego wewnętrznego buforowania, wiele wątków zgłasza w przypadku wyrzucania elementów bezużytecznych serwera i z innych przyczyn.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-126">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="c6e0e-127">W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacje są kumulowane — wszystkie odwołania, które są zgłaszane w przypadku `SurvivingReferences` wywołania zwrotnego w czasie odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="c6e0e-127">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e0e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6e0e-128">Requirements</span></span>  
 <span data-ttu-id="c6e0e-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6e0e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e0e-130">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6e0e-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6e0e-131">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6e0e-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6e0e-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e0e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e0e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6e0e-133">See also</span></span>

- [<span data-ttu-id="c6e0e-134">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c6e0e-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c6e0e-135">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c6e0e-135">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="c6e0e-136">SurvivingReferences2, metoda</span><span class="sxs-lookup"><span data-stu-id="c6e0e-136">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)
