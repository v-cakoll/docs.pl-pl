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
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866094"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="f8d83-102">ICorProfilerCallback::ObjectReferences — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8d83-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="f8d83-103">Powiadamia profiler o obiektach w pamięci, do których odwołuje się określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="f8d83-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8d83-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8d83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8d83-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f8d83-106">podczas Identyfikator obiektu, który odwołuje się do obiektów.</span><span class="sxs-lookup"><span data-stu-id="f8d83-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="f8d83-107">podczas Identyfikator klasy, do której należy wystąpienie określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f8d83-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="f8d83-108">podczas Liczba obiektów przywoływanych przez określony obiekt (czyli liczba elementów w tablicy `objectRefIds`).</span><span class="sxs-lookup"><span data-stu-id="f8d83-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="f8d83-109">podczas Tablica identyfikatorów obiektów, do których odwołują się `objectId`.</span><span class="sxs-lookup"><span data-stu-id="f8d83-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8d83-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8d83-110">Remarks</span></span>  
 <span data-ttu-id="f8d83-111">Metoda `ObjectReferences` jest wywoływana dla każdego obiektu pozostałego w stercie po zakończeniu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="f8d83-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="f8d83-112">Jeśli profiler zwróci błąd z tego wywołania zwrotnego, usługi profilowania będą kontynuowały wywoływanie tego wywołania zwrotnego do momentu kolejnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f8d83-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="f8d83-113">Wywołania zwrotnego `ObjectReferences` można użyć w połączeniu z wywołaniem zwrotnym [ICorProfilerCallback:: RootReferences —](icorprofilercallback-rootreferences-method.md) w celu utworzenia kompletnego grafu odwołań do obiektów dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f8d83-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="f8d83-114">Środowisko uruchomieniowe języka wspólnego (CLR) gwarantuje, że każde odwołanie do obiektu jest raportowane tylko raz przez metodę `ObjectReferences`.</span><span class="sxs-lookup"><span data-stu-id="f8d83-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="f8d83-115">Identyfikatory obiektów zwrócone przez `ObjectReferences` nie są prawidłowe podczas wywołania zwrotnego, ponieważ wyrzucanie elementów bezużytecznych może znajdować się w trakcie przesuwania obiektów.</span><span class="sxs-lookup"><span data-stu-id="f8d83-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="f8d83-116">W związku z tym, nie mogą próbować zbadać obiektów podczas wywołania `ObjectReferences`.</span><span class="sxs-lookup"><span data-stu-id="f8d83-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="f8d83-117">Gdy wywoływana jest [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) , odzyskiwanie pamięci jest kompletne i można bezpiecznie wykonać inspekcję.</span><span class="sxs-lookup"><span data-stu-id="f8d83-117">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="f8d83-118">`ClassId` o wartości null wskazuje, że `objectId` ma typ, który jest wyładowania.</span><span class="sxs-lookup"><span data-stu-id="f8d83-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8d83-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8d83-119">Requirements</span></span>  
 <span data-ttu-id="f8d83-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8d83-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d83-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f8d83-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8d83-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f8d83-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8d83-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d83-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d83-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8d83-124">See also</span></span>

- [<span data-ttu-id="f8d83-125">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8d83-125">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
