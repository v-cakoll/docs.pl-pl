---
title: ICorProfilerCallback2::RootReferences2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2164350ff94e53e6144298aab621065faba4a0dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475349"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="a88dd-102">ICorProfilerCallback2::RootReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="a88dd-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="a88dd-103">Powiadamia program profilujący o odwołaniach do katalogu głównego, po przeprowadzeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a88dd-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="a88dd-104">Ta metoda jest rozszerzeniem [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a88dd-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a88dd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a88dd-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a88dd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a88dd-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="a88dd-107">[in] Liczba elementów w `rootRefIds`, `rootKinds`, `rootFlags`, i `rootIds` tablic.</span><span class="sxs-lookup"><span data-stu-id="a88dd-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="a88dd-108">[in] Tablica obiektów identyfikatorów, każdy z nich odwołuje się do obiektu statycznego lub obiekt na stosie.</span><span class="sxs-lookup"><span data-stu-id="a88dd-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="a88dd-109">Elementy w `rootKinds` tablicy Podaj informacje potrzebne do klasyfikowania odpowiednie elementy w `rootRefIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a88dd-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="a88dd-110">[in] Tablica [cor_prf_gc_root_kind —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) wartości, które wskazują na typ główny kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="a88dd-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="a88dd-111">[in] Tablica [cor_prf_gc_root_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) wartości, które opisują właściwości głównego kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="a88dd-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="a88dd-112">[in] Tablica UINT_PTR wartości tego punktu na liczbę całkowitą, która zawiera dodatkowe informacje na temat głównych kolekcji wyrzucania elementów, w zależności od wartości `rootKinds` parametru.</span><span class="sxs-lookup"><span data-stu-id="a88dd-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="a88dd-113">Jeśli typ główny jest stos, identyfikator katalogu głównego jest dla funkcji, która zawiera zmienną.</span><span class="sxs-lookup"><span data-stu-id="a88dd-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="a88dd-114">Jeśli ten identyfikator główny wynosi 0, funkcja jest bez nazwy funkcji, która jest wewnętrzny środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a88dd-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="a88dd-115">Jeśli typ główny jest uchwytem, identyfikator katalogu głównego wynosi uchwyt kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="a88dd-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="a88dd-116">Dla innych typów głównego Identyfikatora jest nieprzezroczysta wartość i należy ją ignorować.</span><span class="sxs-lookup"><span data-stu-id="a88dd-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a88dd-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a88dd-117">Remarks</span></span>  
 <span data-ttu-id="a88dd-118">`rootRefIds`, `rootKinds`, `rootFlags`, I `rootIds` tablic są tablicami równoległych.</span><span class="sxs-lookup"><span data-stu-id="a88dd-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="a88dd-119">Oznacza to, że `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, i `rootIds[i]` dotyczą wszystkich takim samym certyfikatem głównym.</span><span class="sxs-lookup"><span data-stu-id="a88dd-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="a88dd-120">Zarówno `RootReferences` i `RootReferences2` są wywoływane w celu powiadomić profiler.</span><span class="sxs-lookup"><span data-stu-id="a88dd-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="a88dd-121">Profilery zwykle wdroży jednej lub drugiej metody, ale nie obie, ponieważ informacje są przekazywane w `RootReferences2` jest nadzbiorem, przekazanej `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="a88dd-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="a88dd-122">Istnieje możliwość, że wpisy w `rootRefIds` zero, co oznacza, że główny odwołań ma wartość null i nie odwołuje się do obiektu w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="a88dd-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="a88dd-123">Identyfikatory obiektów są zwracane przez `RootReferences2` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów z stare adresy do nowych adresów.</span><span class="sxs-lookup"><span data-stu-id="a88dd-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="a88dd-124">W związku z tym, profilowania nie należy próbować Zbadaj obiekty podczas `RootReferences2` wywołania.</span><span class="sxs-lookup"><span data-stu-id="a88dd-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="a88dd-125">Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do ich nowych lokalizacji i może być bezpiecznie kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="a88dd-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a88dd-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a88dd-126">Requirements</span></span>  
 <span data-ttu-id="a88dd-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a88dd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a88dd-128">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a88dd-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a88dd-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a88dd-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a88dd-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a88dd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88dd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a88dd-131">See also</span></span>
- [<span data-ttu-id="a88dd-132">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a88dd-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a88dd-133">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a88dd-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
