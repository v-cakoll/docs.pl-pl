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
ms.openlocfilehash: 4141c79502dae89ec228e4e39da121615f292786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782971"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="a2454-102">ICorProfilerCallback::ObjectReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2454-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="a2454-103">Powiadamia program profilujący dotyczących obiektów w pamięci, przywoływane przez określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="a2454-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2454-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2454-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2454-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2454-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a2454-106">[in] Identyfikator obiektu, który odwołuje się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="a2454-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="a2454-107">[in] Identyfikator klasy określony obiekt jest wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="a2454-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="a2454-108">[in] Liczba obiektów, odwołuje się określony obiekt (oznacza to, że liczba elementów w `objectRefIds` tablicy).</span><span class="sxs-lookup"><span data-stu-id="a2454-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="a2454-109">[in] Tablica identyfikatorów obiektów, które odwołują się `objectId`.</span><span class="sxs-lookup"><span data-stu-id="a2454-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2454-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2454-110">Remarks</span></span>  
 <span data-ttu-id="a2454-111">`ObjectReferences` Metoda jest wywoływana dla każdego obiektu, pozostałe w stercie po zakończeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a2454-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="a2454-112">Jeśli program profilujący zwraca błąd z to wywołanie zwrotne, profilowania services zostanie wycofana, wywoływania to wywołanie zwrotne aż do następnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a2454-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="a2454-113">`ObjectReferences` Wywołania zwrotnego mogą być używane w połączeniu z [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) wywołania zwrotnego, aby utworzyć obiekt kompletny wykres odwołań dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a2454-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="a2454-114">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia, że każde odwołanie obiektu jest raportowane tylko raz przez `ObjectReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="a2454-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="a2454-115">Identyfikatory obiektów są zwracane przez `ObjectReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucania elementów bezużytecznych może być w trakcie przenoszenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="a2454-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="a2454-116">W związku z tym, profilowania nie wolno próbować Zbadaj obiekty podczas `ObjectReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="a2454-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="a2454-117">Gdy [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest wywoływana, wyrzucanie elementów zakończeniu zbierania i inspekcji można bezpiecznie wykonać.</span><span class="sxs-lookup"><span data-stu-id="a2454-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="a2454-118">Wartość null `ClassId` wskazuje, że `objectId` ma typ, który jest zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="a2454-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2454-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2454-119">Requirements</span></span>  
 <span data-ttu-id="a2454-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2454-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2454-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2454-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2454-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2454-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2454-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2454-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2454-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2454-124">See also</span></span>

- [<span data-ttu-id="a2454-125">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2454-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
