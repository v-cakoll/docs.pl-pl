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
ms.openlocfilehash: 3cdc185408576f5679daacef4dde438d66e490ff
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862753"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="01ede-102">ICorProfilerInfo2::GetGenerationBounds — Metoda</span><span class="sxs-lookup"><span data-stu-id="01ede-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="01ede-103">Pobiera obszary pamięci, które są segmentami sterty, które tworzą różne generacje wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="01ede-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ede-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01ede-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ede-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01ede-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="01ede-106">podczas Liczba elementów przyznanych przez obiekt wywołujący dla tablicy `ranges`.</span><span class="sxs-lookup"><span data-stu-id="01ede-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="01ede-107">określoną Wskaźnik do liczby całkowitej, która określa łączną liczbę zakresów, część lub wszystkie zostaną zwrócone w tablicy `ranges`.</span><span class="sxs-lookup"><span data-stu-id="01ede-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="01ede-108">określoną Tablica struktur [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , z których każdy opisuje zakres (czyli blok) pamięci w ramach generacji, która nie powoduje wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="01ede-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ede-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01ede-109">Remarks</span></span>  
 <span data-ttu-id="01ede-110">Metodę `GetGenerationBounds` można wywołać z dowolnego wywołania zwrotnego profilera, pod warunkiem, że odzyskiwanie pamięci nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="01ede-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="01ede-111">Większość przesunięć generacji odbywa się podczas odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="01ede-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="01ede-112">Generacji mogą wzrosnąć między kolekcjami, ale zazwyczaj nie można ich przenosić.</span><span class="sxs-lookup"><span data-stu-id="01ede-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="01ede-113">W związku z tym najbardziej interesujące miejsca do wywołania `GetGenerationBounds` są `ICorProfilerCallback2::GarbageCollectionStarted` i `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="01ede-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="01ede-114">Podczas uruchamiania programu niektóre obiekty są przydzielone przez środowisko uruchomieniowe języka wspólnego (CLR), zazwyczaj w generacjach 3 i 0.</span><span class="sxs-lookup"><span data-stu-id="01ede-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="01ede-115">W rezultacie przez kod zarządzany przez czas, te generacje zawierają już obiekty.</span><span class="sxs-lookup"><span data-stu-id="01ede-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="01ede-116">Generacje 1 i 2 zwykle będą puste, z wyjątkiem obiektów fikcyjnych generowanych przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="01ede-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="01ede-117">(Rozmiar fikcyjnych obiektów to 12 bajtów w 32-bitowych implementacjach środowiska CLR; rozmiar jest większy w przypadku implementacji 64-bitowych). Możesz również zobaczyć zakresy generacji 2, które znajdują się w modułach wytwarzanych przez generator obrazu natywnego (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="01ede-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="01ede-118">W takim przypadku obiekty w generacji 2 są *obiektami zablokowanymi*, które są przydzielone podczas uruchamiania programu Ngen. exe, a nie przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="01ede-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="01ede-119">Ta funkcja używa buforów przyznanych przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="01ede-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ede-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01ede-120">Requirements</span></span>  
 <span data-ttu-id="01ede-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ede-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ede-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01ede-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01ede-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01ede-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01ede-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ede-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ede-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01ede-125">See also</span></span>

- [<span data-ttu-id="01ede-126">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="01ede-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="01ede-127">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="01ede-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="01ede-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="01ede-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="01ede-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="01ede-129">Profiling</span></span>](index.md)
