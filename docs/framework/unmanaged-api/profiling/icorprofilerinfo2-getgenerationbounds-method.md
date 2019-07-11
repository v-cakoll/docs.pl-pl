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
ms.openlocfilehash: eee04315e18a6e0442271858b75783a081468f90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776717"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="efd87-102">ICorProfilerInfo2::GetGenerationBounds — Metoda</span><span class="sxs-lookup"><span data-stu-id="efd87-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="efd87-103">Pobiera regiony pamięci, które są segmenty stosu, które składają się na różnych generacji wyrzucania elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="efd87-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efd87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efd87-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="efd87-106">[in] Liczba elementów przydzielonej przez obiekt wywołujący, aby uzyskać `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="efd87-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="efd87-107">[out] Wskaźnik do liczby całkowitej określający łączna liczba zakresów, niektóre lub wszystkie z nich zostaną zwrócone w `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="efd87-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="efd87-108">[out] Tablica [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktur, z których każdy zawiera opis zakresu (czyli bloku) pamięci w generacji, która jest w trakcie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="efd87-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efd87-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efd87-109">Remarks</span></span>  
 <span data-ttu-id="efd87-110">`GetGenerationBounds` Metodę można wywołać z dowolnego wywołania zwrotnego profilera, pod warunkiem, że wyrzucanie elementów bezużytecznych nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="efd87-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="efd87-111">Większość przesunięcie pokoleń ma miejsce podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="efd87-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="efd87-112">Generacje może rosnąć między operacjami, ale zwykle nie zmieniają położenie.</span><span class="sxs-lookup"><span data-stu-id="efd87-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="efd87-113">W związku z tym, najbardziej interesujących miejsc do wywołania `GetGenerationBounds` znajdują się w `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="efd87-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="efd87-114">Podczas uruchamiania programu niektóre obiekty są przydzielane przez środowisko uruchomieniowe języka wspólnego (CLR), zwykle w generacjach 3 i 0.</span><span class="sxs-lookup"><span data-stu-id="efd87-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="efd87-115">W związku z tym według czasu, w kodzie zarządzanym rozpoczyna wykonywanie, generacje te będą już zawierać obiekty.</span><span class="sxs-lookup"><span data-stu-id="efd87-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="efd87-116">Zwykle jest pusta, z wyjątkiem fikcyjnego obiektów, które są generowane przez moduł odśmiecania pamięci generacji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="efd87-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="efd87-117">(Rozmiar obiektów zastępczy jest 12-bajtowy we wdrożeniach 32-bitowe środowisko CLR; rozmiar jest większy we wdrożeniach 64-bitowych). Może być również wyświetlany zakresów generacji 2, które znajdują się w modułach produkowane przez Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="efd87-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="efd87-118">W tym przypadku są obiekty w generacji 2 *mrożone obiekty*, które są przydzielane po uruchomieniu NGen.exe, a nie przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="efd87-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="efd87-119">Ta funkcja używa bufory przypisane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="efd87-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd87-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efd87-120">Requirements</span></span>  
 <span data-ttu-id="efd87-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd87-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd87-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efd87-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efd87-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efd87-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efd87-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd87-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd87-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efd87-125">See also</span></span>

- [<span data-ttu-id="efd87-126">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="efd87-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="efd87-127">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="efd87-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="efd87-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="efd87-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="efd87-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="efd87-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
