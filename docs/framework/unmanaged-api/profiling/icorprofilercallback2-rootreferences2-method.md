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
ms.openlocfilehash: abf92749e1139a85ea2f49fb5d5caff69ce39c24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458464"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="52f88-102">ICorProfilerCallback2::RootReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="52f88-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="52f88-103">Powiadamia profilera odwołania głównego informacje po zakończeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="52f88-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="52f88-104">Ta metoda jest rozszerzeniem [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="52f88-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f88-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="52f88-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52f88-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="52f88-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="52f88-107">[in] Liczba elementów w `rootRefIds`, `rootKinds`, `rootFlags`, i `rootIds` tablic.</span><span class="sxs-lookup"><span data-stu-id="52f88-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="52f88-108">[in] Tablica obiektów identyfikatorów, które odwołuje się do statycznego obiektu albo obiekt na stosie.</span><span class="sxs-lookup"><span data-stu-id="52f88-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="52f88-109">Elementy w `rootKinds` tablicy zawierają informacje do klasyfikowania odpowiednich elementów w `rootRefIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="52f88-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="52f88-110">[in] Tablica [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) wartości, które wskazują na typ główny kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="52f88-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="52f88-111">[in] Tablica [cor_prf_gc_root_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) wartości, które opisują właściwości głównego kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="52f88-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="52f88-112">[in] Tablica UINT_PTR wartości prowadzące do liczba całkowita, która zawiera dodatkowe informacje dotyczące głównego kolekcji odzyskiwanie, w zależności od wartości `rootKinds` parametru.</span><span class="sxs-lookup"><span data-stu-id="52f88-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="52f88-113">Jeśli typ główny stos, identyfikator katalogu głównego jest dla tej funkcji, która zawiera zmienną.</span><span class="sxs-lookup"><span data-stu-id="52f88-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="52f88-114">Jeśli ten identyfikator głównego to 0, ta funkcja jest bez nazwy funkcji, która jest wewnętrzny do środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="52f88-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="52f88-115">Jeśli typu głównego uchwytu, identyfikator katalogu głównego jest na dojście kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="52f88-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="52f88-116">Dla innych typów głównego Identyfikatora jest wartości nieprzezroczystej i należy ją ignorować.</span><span class="sxs-lookup"><span data-stu-id="52f88-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52f88-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52f88-117">Remarks</span></span>  
 <span data-ttu-id="52f88-118">`rootRefIds`, `rootKinds`, `rootFlags`, I `rootIds` tablice są tablice równoległych.</span><span class="sxs-lookup"><span data-stu-id="52f88-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="52f88-119">Oznacza to `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, i `rootIds[i]` wszystkie dotyczą tego samego głównego.</span><span class="sxs-lookup"><span data-stu-id="52f88-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="52f88-120">Zarówno `RootReferences` i `RootReferences2` są wywoływane w celu powiadomienia profilera.</span><span class="sxs-lookup"><span data-stu-id="52f88-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="52f88-121">Profilery będzie zwykle implementowany jednej lub drugiej metody, ale nie oba ponieważ przekazane informacje `RootReferences2` jest nadzbiorem tego przekazano `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="52f88-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="52f88-122">Istnieje możliwość wpisów w `rootRefIds` zero, co oznacza, że odwołanie do odpowiedniego katalogu głównego ma wartość null i nie odwołuje się do obiektu na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="52f88-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="52f88-123">Identyfikatory obiektów zwrócona przez `RootReferences2` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów z stare adresy do nowych adresów.</span><span class="sxs-lookup"><span data-stu-id="52f88-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="52f88-124">W związku z tym profilery nie powinny podejmować próby sprawdź obiekty podczas `RootReferences2` wywołania.</span><span class="sxs-lookup"><span data-stu-id="52f88-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="52f88-125">Gdy [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wszystkie obiekty zostały przeniesione do nowej lokalizacji i może być bezpiecznie kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="52f88-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f88-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52f88-126">Requirements</span></span>  
 <span data-ttu-id="52f88-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f88-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f88-128">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52f88-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52f88-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52f88-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52f88-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f88-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f88-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52f88-131">See Also</span></span>  
 [<span data-ttu-id="52f88-132">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="52f88-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="52f88-133">ICorProfilerCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="52f88-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
