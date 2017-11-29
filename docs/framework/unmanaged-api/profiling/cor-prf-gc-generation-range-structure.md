---
title: "COR_PRF_GC_GENERATION_RANGE — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords: COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2fd546a88f34906ab37e36377f67c26e80b2799
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="7202e-102">COR_PRF_GC_GENERATION_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="7202e-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="7202e-103">Opisuje zakres pamięci, która jest poddawana wyrzucanie elementów bezużytecznych (to znaczy bloku).</span><span class="sxs-lookup"><span data-stu-id="7202e-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7202e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7202e-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="7202e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7202e-105">Members</span></span>  
  
|<span data-ttu-id="7202e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7202e-106">Member</span></span>|<span data-ttu-id="7202e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7202e-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="7202e-108">Wartość [cor_prf_gc_generation —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) wyliczenie określający bloku pamięci generacji, do którego należy.</span><span class="sxs-lookup"><span data-stu-id="7202e-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="7202e-109">Identyfikator obiektu, który określa lokalizację początkową bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="7202e-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="7202e-110">Wskaźnik do liczba całkowita określająca rozmiar używanych część bloku pamięci (to znaczy ilość pamięci użytej w bloku).</span><span class="sxs-lookup"><span data-stu-id="7202e-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="7202e-111">Wskaźnik do liczba całkowita określająca rozmiar bloku pamięci (to znaczy ilość pamięci zarezerwowanej dla bloku).</span><span class="sxs-lookup"><span data-stu-id="7202e-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7202e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7202e-112">Remarks</span></span>  
 <span data-ttu-id="7202e-113">`rangeLength` Gwarancji, wartość jest dokładne tylko wtedy, gdy [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) lub [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), zarówno wykorzystującymi `COR_PRF_GC_GENERATION_RANGE` struktury, jest wywoływana z [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) lub [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7202e-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7202e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7202e-114">Requirements</span></span>  
 <span data-ttu-id="7202e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7202e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7202e-116">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7202e-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7202e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7202e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7202e-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7202e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7202e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7202e-119">See Also</span></span>  
 [<span data-ttu-id="7202e-120">Struktury profilowania</span><span class="sxs-lookup"><span data-stu-id="7202e-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
