---
title: ICorProfilerCallback::ObjectsAllocatedByClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78dde5c50666333c02c8c1a9a167e17af3f40341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454354"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="5b2d0-102">ICorProfilerCallback::ObjectsAllocatedByClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b2d0-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="5b2d0-103">Powiadamia profilera o liczbę wystąpień każdej określonej klasy, które zostały utworzone od czasu ostatniego wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b2d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b2d0-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b2d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b2d0-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="5b2d0-106">[in] Rozmiar `classIds` i `cObjects` tablic.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="5b2d0-107">[in] Tablica klasy identyfikatorów, w którym każdy identyfikator Określa klasę z co najmniej jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="5b2d0-108">[in] Tablica liczb całkowitych, gdzie każdy całkowitą określa liczbę wystąpień odpowiedniej klasy w `classIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b2d0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b2d0-109">Remarks</span></span>  
 <span data-ttu-id="5b2d0-110">`classIds` i `cObjects` tablice są tablice równoległych.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="5b2d0-111">Na przykład `classIds[i]` i `cObjects[i]` odwołania do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="5b2d0-112">Jeśli żadne wystąpienie klasy został utworzony od czasu poprzedniego wyrzucanie elementów bezużytecznych, klasa zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="5b2d0-113">`ObjectsAllocatedByClass` Wywołania zwrotnego nie zgłosi obiekty przydzielone na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="5b2d0-114">Liczby zgłaszanych przez `ObjectsAllocatedByClass` są tylko oszacowania.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="5b2d0-115">Dokładne liczniki można użyć [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="5b2d0-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="5b2d0-116">`classIds` Tablica może zawierać jeden lub więcej wpisów wartości null, jeśli odpowiednie `cObjects` tablica zawiera typy, które są zwalniane.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b2d0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b2d0-117">Requirements</span></span>  
 <span data-ttu-id="5b2d0-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b2d0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b2d0-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b2d0-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b2d0-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b2d0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b2d0-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b2d0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2d0-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b2d0-122">See Also</span></span>  
 [<span data-ttu-id="5b2d0-123">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5b2d0-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
