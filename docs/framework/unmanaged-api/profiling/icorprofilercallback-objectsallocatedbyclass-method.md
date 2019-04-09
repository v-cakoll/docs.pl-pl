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
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195868"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="73630-102">ICorProfilerCallback::ObjectsAllocatedByClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="73630-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="73630-103">Powiadamia program profilujący o liczbę wystąpień każdej określonej klasy, które zostały utworzone od najnowszych wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="73630-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73630-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73630-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="73630-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73630-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="73630-106">[in] Rozmiar `classIds` i `cObjects` tablic.</span><span class="sxs-lookup"><span data-stu-id="73630-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="73630-107">[in] Tablica identyfikatorów, w którym każdy identyfikator Określa klasę z co najmniej jednego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="73630-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="73630-108">[in] Tablica liczb całkowitych, gdzie każda liczba całkowita określa liczbę wystąpień dla odpowiedniej klasy w `classIds` tablicy.</span><span class="sxs-lookup"><span data-stu-id="73630-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73630-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73630-109">Remarks</span></span>  
 <span data-ttu-id="73630-110">`classIds` i `cObjects` tablic są tablicami równoległych.</span><span class="sxs-lookup"><span data-stu-id="73630-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="73630-111">Na przykład `classIds[i]` i `cObjects[i]` odwoływać się do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="73630-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="73630-112">Jeśli żadne wystąpienie klasy został utworzony od czasu poprzedniego wyrzucania elementów bezużytecznych, klasa jest pomijana.</span><span class="sxs-lookup"><span data-stu-id="73630-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="73630-113">`ObjectsAllocatedByClass` Wywołanie zwrotne nie będą zgłaszać obiekty przydzielone w stosie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="73630-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="73630-114">Liczby zgłoszonych przez `ObjectsAllocatedByClass` są jedynie do oszacowania.</span><span class="sxs-lookup"><span data-stu-id="73630-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="73630-115">Dokładna liczba użyć [icorprofilercallback::objectallocated —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="73630-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="73630-116">`classIds` Macierzy może zawierać co najmniej jeden wpis o wartości null, jeśli odpowiedni `cObjects` tablica zawiera typy, które są zwalniane.</span><span class="sxs-lookup"><span data-stu-id="73630-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73630-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73630-117">Requirements</span></span>  
 <span data-ttu-id="73630-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73630-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73630-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73630-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73630-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73630-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="73630-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="73630-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73630-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73630-122">See also</span></span>

- [<span data-ttu-id="73630-123">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="73630-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
