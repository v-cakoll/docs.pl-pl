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
ms.openlocfilehash: ec0f953ecd0b578d25bcbe155f4bec97274e176c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489851"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="8bf59-102">ICorProfilerInfo2::GetGenerationBounds — Metoda</span><span class="sxs-lookup"><span data-stu-id="8bf59-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="8bf59-103">Pobiera regiony pamięci, które są segmenty stosu, które składają się na różnych generacji wyrzucania elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf59-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bf59-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bf59-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="8bf59-106">[in] Liczba elementów przydzielonej przez obiekt wywołujący, aby uzyskać `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8bf59-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="8bf59-107">[out] Wskaźnik do liczby całkowitej określający łączna liczba zakresów, niektóre lub wszystkie z nich zostaną zwrócone w `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8bf59-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="8bf59-108">[out] Tablica [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktur, z których każdy zawiera opis zakresu (czyli bloku) pamięci w generacji, która jest w trakcie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8bf59-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bf59-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bf59-109">Remarks</span></span>  
 <span data-ttu-id="8bf59-110">`GetGenerationBounds` Metodę można wywołać z dowolnego wywołania zwrotnego profilera, pod warunkiem, że wyrzucanie elementów bezużytecznych nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="8bf59-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="8bf59-111">Oznacza to, mogą być wywoływane z dowolnego wywołania zwrotnego, z wyjątkiem tych, które mają miejsce między [icorprofilercallback2::garbagecollectionstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) i [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="8bf59-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="8bf59-112">Większość przesunięcie pokoleń ma miejsce podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8bf59-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="8bf59-113">Generacje może rosnąć między operacjami, ale zwykle nie zmieniają położenie.</span><span class="sxs-lookup"><span data-stu-id="8bf59-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="8bf59-114">W związku z tym, najbardziej interesujących miejsc do wywołania `GetGenerationBounds` znajdują się w `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="8bf59-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="8bf59-115">Podczas uruchamiania programu niektóre obiekty są przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR), zwykle w generacjach 3 i 0.</span><span class="sxs-lookup"><span data-stu-id="8bf59-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="8bf59-116">W związku z tym według czasu, w kodzie zarządzanym rozpoczyna wykonywanie, generacje te będą już zawierać obiekty.</span><span class="sxs-lookup"><span data-stu-id="8bf59-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="8bf59-117">Zwykle jest pusta, z wyjątkiem fikcyjnego obiektów, które są generowane przez moduł odśmiecania pamięci generacji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="8bf59-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="8bf59-118">(Rozmiar obiektów zastępczy jest 12-bajtowy we wdrożeniach 32-bitowe środowisko CLR; rozmiar jest większy we wdrożeniach 64-bitowych). Może być również wyświetlany zakresów generacji 2, które znajdują się w modułach produkowane przez Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="8bf59-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="8bf59-119">W tym przypadku są obiekty w generacji 2 *mrożone obiekty*, które są przydzielane po uruchomieniu NGen.exe, a nie przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bf59-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="8bf59-120">Ta funkcja używa bufory przypisane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8bf59-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf59-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bf59-121">Requirements</span></span>  
 <span data-ttu-id="8bf59-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf59-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf59-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bf59-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bf59-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bf59-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bf59-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf59-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf59-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bf59-126">See also</span></span>
- [<span data-ttu-id="8bf59-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bf59-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="8bf59-128">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bf59-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="8bf59-129">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="8bf59-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="8bf59-130">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="8bf59-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
