---
title: ICorProfilerInfo2::GetObjectGeneration — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: b75de955e3b6857c9cc1b5411df4b0f262c4cb9a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862701"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="7e115-102">ICorProfilerInfo2::GetObjectGeneration — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e115-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="7e115-103">Pobiera segment sterty, która zawiera określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="7e115-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e115-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e115-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e115-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e115-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="7e115-106">podczas Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7e115-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="7e115-107">określoną Wskaźnik do struktury [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , który opisuje zakres (czyli blok) pamięci w ramach generacji, która nie powoduje wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7e115-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="7e115-108">Ten zakres zawiera określony obiekt.</span><span class="sxs-lookup"><span data-stu-id="7e115-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e115-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e115-109">Remarks</span></span>  
 <span data-ttu-id="7e115-110">Metoda `GetObjectGeneration` może być wywoływana z dowolnego wywołania zwrotnego profilera, pod warunkiem, że odzyskiwanie pamięci nie jest w toku.</span><span class="sxs-lookup"><span data-stu-id="7e115-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="7e115-111">Oznacza to, że może być wywoływana z dowolnego wywołania zwrotnego, z wyjątkiem tych, które występują między [ICorProfilerCallback2:: GarbageCollectionStarted —](icorprofilercallback2-garbagecollectionstarted-method.md) i [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e115-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e115-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e115-112">Requirements</span></span>  
 <span data-ttu-id="7e115-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e115-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e115-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7e115-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e115-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7e115-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e115-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e115-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e115-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e115-117">See also</span></span>

- [<span data-ttu-id="7e115-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e115-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7e115-119">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e115-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
