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
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867215"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="2f1bb-102">COR_PRF_GC_GENERATION_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="2f1bb-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="2f1bb-103">Opisuje zakres (czyli blok) pamięci, która jest niedo wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2f1bb-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f1bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f1bb-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="2f1bb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2f1bb-105">Members</span></span>  
  
|<span data-ttu-id="2f1bb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2f1bb-106">Member</span></span>|<span data-ttu-id="2f1bb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2f1bb-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="2f1bb-108">Wartość wyliczenia [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , która określa generację, do której należy blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="2f1bb-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="2f1bb-109">Identyfikator obiektu, który określa lokalizację początkową bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="2f1bb-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="2f1bb-110">Wskaźnik do liczby całkowitej, która określa rozmiar używanej części bloku pamięci (czyli ilość pamięci używanej w bloku).</span><span class="sxs-lookup"><span data-stu-id="2f1bb-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="2f1bb-111">Wskaźnik do liczby całkowitej, która określa rozmiar bloku pamięci (czyli ilość pamięci zarezerwowanej dla bloku).</span><span class="sxs-lookup"><span data-stu-id="2f1bb-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f1bb-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f1bb-112">Remarks</span></span>  
 <span data-ttu-id="2f1bb-113">Wartość `rangeLength` ma być dokładna tylko wtedy, gdy [ICorProfilerInfo2:: GetGenerationBounds —](icorprofilerinfo2-getgenerationbounds-method.md) lub [ICorProfilerInfo2:: GetObjectGeneration —](icorprofilerinfo2-getobjectgeneration-method.md), z których obie używają struktury `COR_PRF_GC_GENERATION_RANGE`, jest wywoływana z metody [ICorProfilerCallback2:: GarbageCollectionStarted —](icorprofilercallback2-garbagecollectionstarted-method.md) lub [ICorProfilerCallback2:: GarbageCollectionFinished —](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2f1bb-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f1bb-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f1bb-114">Requirements</span></span>  
 <span data-ttu-id="2f1bb-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f1bb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f1bb-116">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="2f1bb-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2f1bb-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f1bb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f1bb-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f1bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1bb-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f1bb-119">See also</span></span>

- [<span data-ttu-id="2f1bb-120">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="2f1bb-120">Profiling Structures</span></span>](profiling-structures.md)
