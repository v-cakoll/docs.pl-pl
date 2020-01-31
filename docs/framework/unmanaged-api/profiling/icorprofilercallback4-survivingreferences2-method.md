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
ms.openlocfilehash: bec50183e6a8690cb02f3dc06d32b7449e055cea
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865171"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="fb195-102">ICorProfilerCallback4::SurvivingReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb195-102">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>
<span data-ttu-id="fb195-103">Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fb195-103">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="fb195-104">Ta metoda jest wywoływana, jeśli Profiler zaimplementuje Interfejs [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fb195-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="fb195-105">To wywołanie zwrotne zastępuje metodę [ICorProfilerCallback2:: SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md) , ponieważ umożliwia raportowanie większych zakresów obiektów, których długość przekracza, co może być wyrażone w ulong.</span><span class="sxs-lookup"><span data-stu-id="fb195-105">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb195-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb195-106">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb195-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb195-107">Parameters</span></span>  
 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="fb195-108">podczas Liczba bloków ciągłych obiektów, które przeżyły jako wynik niekompaktowego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fb195-108">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="fb195-109">Oznacza to, że wartość `cSurvivingObjectIDRanges` jest rozmiarem `objectIDRangeStart` i `cObjectIDRangeLength` tablic, które przechowują odpowiednio `ObjectID` i długość dla każdego bloku obiektów.</span><span class="sxs-lookup"><span data-stu-id="fb195-109">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="fb195-110">Dwa następne argumenty `SurvivingReferences2` są tablicami równoległymi.</span><span class="sxs-lookup"><span data-stu-id="fb195-110">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="fb195-111">Innymi słowy, `objectIDRangeStart` i `cObjectIDRangeLength` dotyczą tego samego bloku ciągłego obiektów.</span><span class="sxs-lookup"><span data-stu-id="fb195-111">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="fb195-112">podczas Tablica wartości `ObjectID`, z których każdy jest adresem początkowym bloku ciągłego, na żywo obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fb195-112">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="fb195-113">podczas Tablica liczb całkowitych, z których każdy jest rozmiarem ciągłego bloku ciągłych obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fb195-113">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="fb195-114">Rozmiar jest określony dla każdego bloku, do którego odwołuje się tablica `objectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="fb195-114">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb195-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb195-115">Remarks</span></span>  
 <span data-ttu-id="fb195-116">Elementy `objectIDRangeStart` i `cObjectIDRangeLength` tablice powinny być interpretowane w następujący sposób, aby określić, czy obiekt przeżyje odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="fb195-116">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="fb195-117">Załóżmy, że wartość `ObjectID` (`ObjectID`) znajduje się w następującym zakresie:</span><span class="sxs-lookup"><span data-stu-id="fb195-117">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="fb195-118">Dla każdej wartości `i`, która znajduje się w następującym zakresie, obiekt przeżyłył wyrzucanie elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="fb195-118">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="fb195-119">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="fb195-119">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="fb195-120">Niekompaktowe wyrzucanie elementów bezużytecznych przejmuje pamięć zajmowaną przez obiekty "martwe", ale nie kompaktuje ilości wolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="fb195-120">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="fb195-121">W efekcie do sterty jest zwracana pamięć, ale nie są przenoszone żadne obiekty "na żywo".</span><span class="sxs-lookup"><span data-stu-id="fb195-121">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="fb195-122">Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `SurvivingReferences2` dla niekompaktowych kolekcji elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fb195-122">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="fb195-123">W przypadku kompaktowania kolekcji elementów bezużytecznych jest wywoływana [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fb195-123">For compacting garbage collections, [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="fb195-124">Pojedyncze wyrzucanie elementów bezużytecznych może być kompaktowania dla jednej generacji i niekompaktowania dla innych.</span><span class="sxs-lookup"><span data-stu-id="fb195-124">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="fb195-125">W przypadku wyrzucania elementów bezużytecznych dla każdej konkretnej generacji Profiler otrzyma wywołanie zwrotne `SurvivingReferences2` lub wywołanie zwrotne [MovedReferences2 —](icorprofilercallback4-movedreferences2-method.md) , ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="fb195-125">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="fb195-126">Podczas konkretnego wyrzucania elementów bezużytecznych może zostać odebranych wiele `SurvivingReferences2` wywołań zwrotnych z powodu ograniczonego wewnętrznego buforowania, wielu wywołań zwrotnych podczas odzyskiwania pamięci serwera i innych przyczyn.</span><span class="sxs-lookup"><span data-stu-id="fb195-126">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="fb195-127">W przypadku wielu wywołań zwrotnych podczas wyrzucania elementów bezużytecznych informacja jest zbiorcza; wszystkie odwołania, które są zgłaszane w dowolnym `SurvivingReferences2` wywołanie zwrotne przeżyły do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fb195-127">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="fb195-128">Jeśli profiler implementuje zarówno interfejsy [ICorProfilerCallback](icorprofilercallback-interface.md) , jak i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , Metoda `SurvivingReferences2` jest wywoływana przed metodą [ICorProfilerCallback2:: SurvivingReferences —](icorprofilercallback2-survivingreferences-method.md) , ale tylko wtedy, gdy `SurvivingReferences2` zwróci się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fb195-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="fb195-129">Preplikcy mogą zwracać wynik HRESULT, który wskazuje niepowodzenie z metody `SurvivingReferences2`, aby uniknąć wywoływania drugiej metody.</span><span class="sxs-lookup"><span data-stu-id="fb195-129">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb195-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb195-130">Requirements</span></span>  
 <span data-ttu-id="fb195-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb195-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb195-132">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fb195-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb195-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fb195-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb195-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb195-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb195-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb195-135">See also</span></span>

- [<span data-ttu-id="fb195-136">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb195-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fb195-137">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb195-137">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="fb195-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb195-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
