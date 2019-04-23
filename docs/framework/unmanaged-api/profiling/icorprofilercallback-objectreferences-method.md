---
title: ICorProfilerCallback::ObjectReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119252"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="c40ca-102">ICorProfilerCallback::ObjectReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="c40ca-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="c40ca-103">Powiadamia program profilujący dotyczących obiektów w pamięci, przywoływane przez określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="c40ca-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c40ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c40ca-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c40ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c40ca-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="c40ca-106">[in] Identyfikator obiektu, który odwołuje się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="c40ca-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="c40ca-107">[in] Identyfikator klasy określony obiekt jest wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="c40ca-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="c40ca-108">[in] Liczba obiektów, odwołuje się określony obiekt (oznacza to, że liczba elementów w `objectRefIds` tablicy).</span><span class="sxs-lookup"><span data-stu-id="c40ca-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="c40ca-109">[in] Tablica identyfikatorów obiektów, które odwołują się `objectId`.</span><span class="sxs-lookup"><span data-stu-id="c40ca-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c40ca-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c40ca-110">Remarks</span></span>  
 <span data-ttu-id="c40ca-111">`ObjectReferences` Metoda jest wywoływana dla każdego obiektu, pozostałe w stercie po zakończeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c40ca-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="c40ca-112">Jeśli program profilujący zwraca błąd z to wywołanie zwrotne, profilowania services zostanie wycofana, wywoływania to wywołanie zwrotne aż do następnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c40ca-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="c40ca-113">`ObjectReferences` Wywołania zwrotnego mogą być używane w połączeniu z [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) wywołania zwrotnego, aby utworzyć obiekt kompletny wykres odwołań dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c40ca-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="c40ca-114">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia, że każde odwołanie obiektu jest raportowane tylko raz przez `ObjectReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="c40ca-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="c40ca-115">Identyfikatory obiektów są zwracane przez `ObjectReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="c40ca-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="c40ca-116">W związku z tym, profilowania nie wolno próbować Zbadaj obiekty podczas `ObjectReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="c40ca-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="c40ca-117">Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wyrzucanie elementów zakończeniu zbierania i inspekcji można bezpiecznie wykonać.</span><span class="sxs-lookup"><span data-stu-id="c40ca-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="c40ca-118">Wartość null `ClassId` wskazuje, że `objectId` ma typ, który jest zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="c40ca-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c40ca-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c40ca-119">Requirements</span></span>  
 <span data-ttu-id="c40ca-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c40ca-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c40ca-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c40ca-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c40ca-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c40ca-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c40ca-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c40ca-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c40ca-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c40ca-124">See also</span></span>

- [<span data-ttu-id="c40ca-125">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c40ca-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
