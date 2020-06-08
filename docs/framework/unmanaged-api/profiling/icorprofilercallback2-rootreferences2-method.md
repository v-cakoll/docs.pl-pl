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
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499756"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="64e0c-102">ICorProfilerCallback2::RootReferences2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="64e0c-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="64e0c-103">Powiadamia profiler o odwołaniach głównych po wystąpieniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="64e0c-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="64e0c-104">Ta metoda jest rozszerzeniem metody [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="64e0c-104">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e0c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="64e0c-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64e0c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="64e0c-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="64e0c-107">podczas Liczba elementów w `rootRefIds` tablicach,, `rootKinds` `rootFlags` i `rootIds` .</span><span class="sxs-lookup"><span data-stu-id="64e0c-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="64e0c-108">podczas Tablica identyfikatorów obiektów, z których każdy odwołuje się do obiektu statycznego lub obiektu na stosie.</span><span class="sxs-lookup"><span data-stu-id="64e0c-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="64e0c-109">Elementy w `rootKinds` tablicy zawierają informacje do klasyfikowania odpowiadających im elementów w `rootRefIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="64e0c-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="64e0c-110">podczas Tablica wartości [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) , które wskazują typ elementu głównego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="64e0c-110">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="64e0c-111">podczas Tablica wartości [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) , które opisują właściwości katalogu głównego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="64e0c-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="64e0c-112">podczas Tablica wartości UINT_PTR, która wskazuje liczbę całkowitą, która zawiera dodatkowe informacje o katalogu głównym wyrzucania elementów bezużytecznych, w zależności od wartości `rootKinds` parametru.</span><span class="sxs-lookup"><span data-stu-id="64e0c-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="64e0c-113">Jeśli typ elementu głównego to stos, identyfikator główny jest dla funkcji, która zawiera zmienną.</span><span class="sxs-lookup"><span data-stu-id="64e0c-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="64e0c-114">Jeśli ten identyfikator główny to 0, funkcja jest nienazwaną funkcją, która jest wewnętrzna dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="64e0c-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="64e0c-115">Jeśli typ elementu głównego to dojście, identyfikator główny jest dla dojścia do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="64e0c-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="64e0c-116">W przypadku innych typów głównych identyfikator jest wartością nieprzezroczystą i powinien zostać zignorowany.</span><span class="sxs-lookup"><span data-stu-id="64e0c-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64e0c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64e0c-117">Remarks</span></span>  
 <span data-ttu-id="64e0c-118">`rootRefIds`Tablice, `rootKinds` , `rootFlags` i `rootIds` są tablicami równoległymi.</span><span class="sxs-lookup"><span data-stu-id="64e0c-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="64e0c-119">To jest,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` i `rootIds[i]` wszystko dotyczy tego samego katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="64e0c-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="64e0c-120">Oba `RootReferences` i `RootReferences2` są wywoływane w celu powiadomienia profilera.</span><span class="sxs-lookup"><span data-stu-id="64e0c-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="64e0c-121">Profilowający zwykle implementują jedną metodę lub drugą, ale nie obie, ponieważ przesyłane informacje `RootReferences2` są podzbiorem, który przeszedł `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="64e0c-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="64e0c-122">Istnieje możliwość, że wpisy w `rootRefIds` wartości są równe zero, co oznacza, że odpowiadające mu odwołanie główne ma wartość null i nie odwołuje się do obiektu w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="64e0c-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="64e0c-123">Identyfikatory obiektów zwrócone przez `RootReferences2` nie są prawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może być w trakcie przeniesienia obiektów ze starych adresów na nowe adresy.</span><span class="sxs-lookup"><span data-stu-id="64e0c-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="64e0c-124">W związku z tym nie należy próbować kontrolować obiektów podczas `RootReferences2` wywołania.</span><span class="sxs-lookup"><span data-stu-id="64e0c-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="64e0c-125">Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , wszystkie obiekty zostały przeniesione do nowych lokalizacji i można je bezpiecznie sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="64e0c-125">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e0c-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64e0c-126">Requirements</span></span>  
 <span data-ttu-id="64e0c-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64e0c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e0c-128">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="64e0c-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64e0c-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="64e0c-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64e0c-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64e0c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e0c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64e0c-131">See also</span></span>

- [<span data-ttu-id="64e0c-132">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64e0c-132">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="64e0c-133">ICorProfilerCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64e0c-133">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
