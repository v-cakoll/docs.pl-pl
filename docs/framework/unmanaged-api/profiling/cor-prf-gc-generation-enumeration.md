---
title: COR_PRF_GC_GENERATION — Wyliczenie
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15bd3ed8f1642e44ecf9c4df49feebd72eeac8c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590136"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="7c257-102">COR_PRF_GC_GENERATION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7c257-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="7c257-103">Identyfikuje generacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7c257-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c257-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c257-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="7c257-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7c257-105">Members</span></span>  
  
|<span data-ttu-id="7c257-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7c257-106">Member</span></span>|<span data-ttu-id="7c257-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7c257-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="7c257-108">Obiekt jest przechowywany jako generacji 0.</span><span class="sxs-lookup"><span data-stu-id="7c257-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="7c257-109">Obiekt jest przechowywany jako generacji 1.</span><span class="sxs-lookup"><span data-stu-id="7c257-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="7c257-110">Obiekt jest przechowywany jako generacji 2.</span><span class="sxs-lookup"><span data-stu-id="7c257-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="7c257-111">Obiekt jest przechowywany w stosie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c257-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c257-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c257-112">Remarks</span></span>  
 <span data-ttu-id="7c257-113">Moduł odśmiecania pamięci zwiększa wydajność zarządzania pamięcią, dzieląc obiektów na generacje, w oparciu o wieku.</span><span class="sxs-lookup"><span data-stu-id="7c257-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="7c257-114">Moduł zbierający elementy bezużyteczne aktualnie używa trzy generacje, numerowane 0, 1 i 2 oraz segment specjalne sterty, który jest używany w przypadku dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="7c257-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="7c257-115">Obiekty, których rozmiar przekracza określoną wartość są przechowywane w stosie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c257-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="7c257-116">Inne obiekty przydzielone zaczynają należące do generacji 0.</span><span class="sxs-lookup"><span data-stu-id="7c257-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="7c257-117">Wszystkie obiekty znajdujące się po wyrzucanie elementów bezużytecznych występuje w generacji 0 są promowane do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="7c257-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="7c257-118">Obiekty, znajdujące się po wystąpieniu wyrzucania elementów bezużytecznych w generacji 1 są przenoszone do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="7c257-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="7c257-119">Korzystanie z generacji oznacza, że moduł zbierający elementy bezużyteczne musi pracować tylko podzbiór przydzielone obiekty w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="7c257-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="7c257-120">`COR_PRF_GC_GENERATION` Wyliczenie jest używane przez [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="7c257-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c257-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c257-121">Requirements</span></span>  
 <span data-ttu-id="7c257-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c257-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c257-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c257-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c257-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c257-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c257-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c257-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c257-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c257-126">See also</span></span>
- [<span data-ttu-id="7c257-127">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7c257-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
