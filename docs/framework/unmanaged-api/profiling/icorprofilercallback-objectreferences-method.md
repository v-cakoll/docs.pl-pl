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
ms.openlocfilehash: e64eeff8ef80aa264c9c49bd12a0cc45e0da18a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461890"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="1aaea-102">ICorProfilerCallback::ObjectReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="1aaea-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="1aaea-103">Powiadamia profilera dotyczących obiektów w pamięci, które są przywoływane przez określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="1aaea-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aaea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1aaea-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1aaea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1aaea-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="1aaea-106">[in] Identyfikator obiektu, który odwołuje się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="1aaea-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="1aaea-107">[in] Identyfikator klasy określony obiekt jest wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="1aaea-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="1aaea-108">[in] Liczba obiektów odwołuje się określony obiekt (to znaczy, że liczba elementów w `objectRefIds` tablicy).</span><span class="sxs-lookup"><span data-stu-id="1aaea-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="1aaea-109">[in] Tablicę identyfikatorów obiektów, które są przywoływane przez `objectId`.</span><span class="sxs-lookup"><span data-stu-id="1aaea-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aaea-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1aaea-110">Remarks</span></span>  
 <span data-ttu-id="1aaea-111">`ObjectReferences` Metoda jest wywoływana dla każdego obiektu pozostałych sterty po zakończeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1aaea-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="1aaea-112">Jeśli profilera zwraca błąd, to wywołanie zwrotne, usług profilowania nie będzie kontynuowane wywoływania tego wywołania zwrotnego do czasu następnego wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1aaea-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="1aaea-113">`ObjectReferences` Wywołania zwrotnego można używać w połączeniu z [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) wywołanie zwrotne do utworzenia wykres odwołanie cały obiekt środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1aaea-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="1aaea-114">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia, że odwołanie do każdego obiektu jest raportowane tylko raz przez `ObjectReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="1aaea-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="1aaea-115">Identyfikatory obiektów zwrócona przez `ObjectReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="1aaea-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="1aaea-116">W związku z tym profilowania nie wolno próbować sprawdzić obiekty podczas `ObjectReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="1aaea-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="1aaea-117">Gdy [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest nazywany odzyskiwanie kolekcji została zakończona i inspekcji można bezpiecznie wykonać.</span><span class="sxs-lookup"><span data-stu-id="1aaea-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="1aaea-118">Wartość null `ClassId` oznacza to, że `objectId` ma typ, który jest zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="1aaea-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aaea-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1aaea-119">Requirements</span></span>  
 <span data-ttu-id="1aaea-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aaea-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aaea-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1aaea-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1aaea-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aaea-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aaea-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aaea-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aaea-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aaea-124">See Also</span></span>  
 [<span data-ttu-id="1aaea-125">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1aaea-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
