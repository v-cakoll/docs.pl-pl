---
title: COR_PRF_GC_GENERATION_RANGE — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: 0bdb8cd02e0beb69e3ec594b0aadd741a5f0d924
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428332"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="67bd0-102">COR_PRF_GC_GENERATION_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="67bd0-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="67bd0-103">Opisuje zakres (czyli blok) pamięci, która jest niedo wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="67bd0-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67bd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67bd0-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="67bd0-105">Members</span><span class="sxs-lookup"><span data-stu-id="67bd0-105">Members</span></span>  
  
|<span data-ttu-id="67bd0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="67bd0-106">Member</span></span>|<span data-ttu-id="67bd0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="67bd0-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="67bd0-108">Wartość wyliczenia [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) , która określa generację, do której należy blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="67bd0-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="67bd0-109">Identyfikator obiektu, który określa lokalizację początkową bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="67bd0-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="67bd0-110">Wskaźnik do liczby całkowitej, która określa rozmiar używanej części bloku pamięci (czyli ilość pamięci używanej w bloku).</span><span class="sxs-lookup"><span data-stu-id="67bd0-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="67bd0-111">Wskaźnik do liczby całkowitej, która określa rozmiar bloku pamięci (czyli ilość pamięci zarezerwowanej dla bloku).</span><span class="sxs-lookup"><span data-stu-id="67bd0-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67bd0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67bd0-112">Remarks</span></span>  
 <span data-ttu-id="67bd0-113">Wartość `rangeLength` ma być dokładna tylko wtedy, gdy [ICorProfilerInfo2:: GetGenerationBounds —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) lub [ICorProfilerInfo2:: GetObjectGeneration —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), z których obie używają struktury `COR_PRF_GC_GENERATION_RANGE`, jest wywoływana z metody [ICorProfilerCallback2:: GarbageCollectionStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) lub [ICorProfilerCallback2:: GarbageCollectionFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="67bd0-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67bd0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67bd0-114">Requirements</span></span>  
 <span data-ttu-id="67bd0-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67bd0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67bd0-116">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="67bd0-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="67bd0-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="67bd0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67bd0-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67bd0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67bd0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67bd0-119">See also</span></span>

- [<span data-ttu-id="67bd0-120">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="67bd0-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
