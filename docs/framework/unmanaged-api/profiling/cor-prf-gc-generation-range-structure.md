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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 646c4e37a7fab503a26557f9fdfc926b1186b17b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216707"
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="ef4be-102">COR_PRF_GC_GENERATION_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="ef4be-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="ef4be-103">W tym artykule opisano szeroką gamę (czyli bloku) pamięci, która jest w trakcie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ef4be-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef4be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef4be-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="ef4be-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ef4be-105">Members</span></span>  
  
|<span data-ttu-id="ef4be-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ef4be-106">Member</span></span>|<span data-ttu-id="ef4be-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef4be-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="ef4be-108">Wartość [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) wyliczenie, które określa blok pamięci generacji, do której należy.</span><span class="sxs-lookup"><span data-stu-id="ef4be-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="ef4be-109">Identyfikator obiektu, który określa lokalizację początkową bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="ef4be-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="ef4be-110">Wskaźnik na liczbę całkowitą, która określa rozmiar użytej części bloku pamięci (oznacza to, ilości pamięci używanej w ramach bloku).</span><span class="sxs-lookup"><span data-stu-id="ef4be-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="ef4be-111">Wskaźnik na liczbę całkowitą, która określa rozmiar bloku pamięci (oznacza to, że ilość pamięci zarezerwowanej dla bloku).</span><span class="sxs-lookup"><span data-stu-id="ef4be-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef4be-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef4be-112">Remarks</span></span>  
 <span data-ttu-id="ef4be-113">`rangeLength` Być dokładna wartość jest wyświetlana tylko wtedy, gdy [icorprofilerinfo2::getgenerationbounds —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) lub [icorprofilerinfo2::getobjectgeneration —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), obie wykorzystującymi `COR_PRF_GC_GENERATION_RANGE` struktury, jest wywoływana z [icorprofilercallback2::garbagecollectionstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) lub [icorprofilercallback2::garbagecollectionfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ef4be-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef4be-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef4be-114">Requirements</span></span>  
 <span data-ttu-id="ef4be-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef4be-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef4be-116">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ef4be-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ef4be-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef4be-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef4be-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef4be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef4be-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef4be-119">See also</span></span>

- [<span data-ttu-id="ef4be-120">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="ef4be-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
