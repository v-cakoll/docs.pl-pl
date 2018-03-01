---
title: "COR_PRF_GC_GENERATION — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69eec0c2dfccacee4c54c9f2493da523812259aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="e3db6-102">COR_PRF_GC_GENERATION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e3db6-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="e3db6-103">Określa Generowanie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e3db6-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3db6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3db6-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="e3db6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3db6-105">Members</span></span>  
  
|<span data-ttu-id="e3db6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3db6-106">Member</span></span>|<span data-ttu-id="e3db6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3db6-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="e3db6-108">Obiekt jest przechowywany jako generacji 0.</span><span class="sxs-lookup"><span data-stu-id="e3db6-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="e3db6-109">Obiekt jest przechowywany jako generacji 1.</span><span class="sxs-lookup"><span data-stu-id="e3db6-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="e3db6-110">Obiekt jest przechowywany jako generacji 2.</span><span class="sxs-lookup"><span data-stu-id="e3db6-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="e3db6-111">Obiekt jest przechowywany w sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3db6-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3db6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3db6-112">Remarks</span></span>  
 <span data-ttu-id="e3db6-113">Moduł zbierający elementy bezużyteczne zwiększa wydajność zarządzania pamięcią przez obiekty podziału do generacje oparte na wieku.</span><span class="sxs-lookup"><span data-stu-id="e3db6-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="e3db6-114">Moduł zbierający elementy bezużyteczne aktualnie używa trzy generacje numerowane 0, 1, 2, a także segment specjalne stosu, który jest używany dla dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="e3db6-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="e3db6-115">Obiekty, którego rozmiar jest większy niż określonej wartości są przechowywane w sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3db6-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="e3db6-116">Inne obiekty przydzielone uruchamiane należących do generacji 0.</span><span class="sxs-lookup"><span data-stu-id="e3db6-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="e3db6-117">Wszystkie obiekty znajdujące się po wyrzucania podczas generowania 0 awansowane na pokolenie 1.</span><span class="sxs-lookup"><span data-stu-id="e3db6-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="e3db6-118">Przenieś obiekty znajdujące się po wyrzucania podczas generowania 1 do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="e3db6-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="e3db6-119">Użycie generacje oznacza, że moduł zbierający elementy bezużyteczne ma do pracy z tylko podzestaw przydzielone obiekty w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="e3db6-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="e3db6-120">`COR_PRF_GC_GENERATION` Wyliczenie jest używany przez [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="e3db6-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3db6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3db6-121">Requirements</span></span>  
 <span data-ttu-id="e3db6-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3db6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3db6-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3db6-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3db6-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3db6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3db6-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3db6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3db6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3db6-126">See Also</span></span>  
 [<span data-ttu-id="e3db6-127">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e3db6-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
