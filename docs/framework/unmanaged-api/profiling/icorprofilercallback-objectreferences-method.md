---
title: "ICorProfilerCallback::ObjectReferences — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdebc1984f86d3801759f8f987df8fb89d82e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="a220b-102">ICorProfilerCallback::ObjectReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="a220b-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="a220b-103">Powiadamia profilera dotyczących obiektów w pamięci, które są przywoływane przez określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="a220b-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a220b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a220b-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a220b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a220b-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a220b-106">[in] Identyfikator obiektu, który odwołuje się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="a220b-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="a220b-107">[in] Identyfikator klasy określony obiekt jest wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="a220b-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="a220b-108">[in] Liczba obiektów odwołuje się określony obiekt (to znaczy, że liczba elementów w `objectRefIds` tablicy).</span><span class="sxs-lookup"><span data-stu-id="a220b-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="a220b-109">[in] Tablicę identyfikatorów obiektów, które są przywoływane przez `objectId`.</span><span class="sxs-lookup"><span data-stu-id="a220b-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a220b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a220b-110">Remarks</span></span>  
 <span data-ttu-id="a220b-111">`ObjectReferences` Metoda jest wywoływana dla każdego obiektu pozostałych sterty po zakończeniu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a220b-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="a220b-112">Jeśli profilera zwraca błąd, to wywołanie zwrotne, usług profilowania nie będzie kontynuowane wywoływania tego wywołania zwrotnego do czasu następnego wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a220b-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="a220b-113">`ObjectReferences` Wywołania zwrotnego można używać w połączeniu z [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) wywołanie zwrotne do utworzenia wykres odwołanie cały obiekt środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a220b-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="a220b-114">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia, że odwołanie do każdego obiektu jest raportowane tylko raz przez `ObjectReferences` metody.</span><span class="sxs-lookup"><span data-stu-id="a220b-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="a220b-115">Identyfikatory obiektów zwrócona przez `ObjectReferences` są nieprawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w środku przenoszenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="a220b-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="a220b-116">W związku z tym profilowania nie wolno próbować sprawdzić obiekty podczas `ObjectReferences` wywołania.</span><span class="sxs-lookup"><span data-stu-id="a220b-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="a220b-117">Gdy [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) jest nazywany odzyskiwanie kolekcji została zakończona i inspekcji można bezpiecznie wykonać.</span><span class="sxs-lookup"><span data-stu-id="a220b-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="a220b-118">Wartość null `ClassId` oznacza to, że `objectId` ma typ, który jest zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="a220b-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a220b-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a220b-119">Requirements</span></span>  
 <span data-ttu-id="a220b-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a220b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a220b-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a220b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a220b-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a220b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a220b-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a220b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a220b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a220b-124">See Also</span></span>  
 [<span data-ttu-id="a220b-125">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="a220b-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
