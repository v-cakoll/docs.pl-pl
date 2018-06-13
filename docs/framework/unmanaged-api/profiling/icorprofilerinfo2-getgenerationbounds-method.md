---
title: ICorProfilerInfo2::GetGenerationBounds — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cfac1304a3d60a418065e4fc2994705548eeac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458441"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="1b1ff-102">ICorProfilerInfo2::GetGenerationBounds — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1ff-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="1b1ff-103">Pobiera regiony pamięci, które są segmentów sterty, wchodzące w skład różnych generacji wyrzucania elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b1ff-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b1ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b1ff-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="1b1ff-106">[in] Liczba elementów przydzielone przez obiekt wywołujący dla `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="1b1ff-107">[out] Wskaźnik do wartości całkowitej, łączna liczba zakresów, który określa niektóre lub wszystkie z nich zostaną zwrócone w `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="1b1ff-108">[out] Tablica [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, z których każdy zawiera opis zakresu (to znaczy bloku) pamięci w ramach wybranej generacji jest poddawana wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b1ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b1ff-109">Remarks</span></span>  
 <span data-ttu-id="1b1ff-110">`GetGenerationBounds` Można wywołać metody zwrotne profilera, pod warunkiem, że pamięci nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="1b1ff-111">Oznacza to, może zostać wywołana z dowolnego wywołania zwrotnego z wyjątkiem tych, które mają miejsce między [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="1b1ff-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="1b1ff-112">Większość zmieni pokoleń odbywa się podczas odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="1b1ff-113">Generacje mogą rosnąć między kolekcji, ale zwykle nie należy przenosić.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="1b1ff-114">W związku z tym najbardziej interesujące miejsca do wywołania `GetGenerationBounds` w `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="1b1ff-115">Podczas uruchamiania programu niektóre obiekty są przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR), zazwyczaj w generacje 3 i 0.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="1b1ff-116">W związku z tym w czasie kodu zarządzanego rozpoczyna wykonywanie tych generacje już będzie zawierać obiektów.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="1b1ff-117">Zwykle jest pusta, z wyjątkiem fikcyjny obiektów, które są generowane przez moduł garbage collector generacji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="1b1ff-118">(Rozmiar fikcyjny obiektów jest 12 bajtów w implementacjach 32-bitowego środowiska CLR; rozmiar jest większy w implementacjach 64-bitowe). Może być również wyświetlany zakresy generacji 2, które znajdują się wewnątrz modułów utworzonego przez Generator obrazu natywnego (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="1b1ff-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="1b1ff-119">W takim przypadku obiekt w generacji 2 są *zablokowane obiekty*, które są przydzielane po uruchomieniu NGen.exe, a nie przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="1b1ff-120">Ta funkcja korzysta buforów przydzielone przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="1b1ff-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1ff-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b1ff-121">Requirements</span></span>  
 <span data-ttu-id="1b1ff-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1ff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1ff-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b1ff-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b1ff-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b1ff-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1ff-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1ff-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b1ff-126">See Also</span></span>  
 [<span data-ttu-id="1b1ff-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b1ff-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="1b1ff-128">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b1ff-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="1b1ff-129">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="1b1ff-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="1b1ff-130">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="1b1ff-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
