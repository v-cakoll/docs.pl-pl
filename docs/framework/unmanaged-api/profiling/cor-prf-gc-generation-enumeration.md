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
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775079"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="b4837-102">COR_PRF_GC_GENERATION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b4837-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="b4837-103">Identyfikuje generacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b4837-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4837-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4837-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="b4837-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b4837-105">Members</span></span>  
  
|<span data-ttu-id="b4837-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b4837-106">Member</span></span>|<span data-ttu-id="b4837-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4837-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="b4837-108">Obiekt jest przechowywany jako generacji 0.</span><span class="sxs-lookup"><span data-stu-id="b4837-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="b4837-109">Obiekt jest przechowywany jako generacji 1.</span><span class="sxs-lookup"><span data-stu-id="b4837-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="b4837-110">Obiekt jest przechowywany jako generacji 2.</span><span class="sxs-lookup"><span data-stu-id="b4837-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="b4837-111">Obiekt jest przechowywany w stosie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4837-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4837-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4837-112">Remarks</span></span>  
 <span data-ttu-id="b4837-113">Moduł odśmiecania pamięci zwiększa wydajność zarządzania pamięcią, dzieląc obiektów na generacje, w oparciu o wieku.</span><span class="sxs-lookup"><span data-stu-id="b4837-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="b4837-114">Moduł zbierający elementy bezużyteczne aktualnie używa trzy generacje, numerowane 0, 1 i 2 oraz segment specjalne sterty, który jest używany w przypadku dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="b4837-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="b4837-115">Obiekty, których rozmiar przekracza określoną wartość są przechowywane w stosie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4837-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="b4837-116">Inne obiekty przydzielone zaczynają należące do generacji 0.</span><span class="sxs-lookup"><span data-stu-id="b4837-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="b4837-117">Wszystkie obiekty znajdujące się po wyrzucanie elementów bezużytecznych występuje w generacji 0 są promowane do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="b4837-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="b4837-118">Obiekty, znajdujące się po wystąpieniu wyrzucania elementów bezużytecznych w generacji 1 są przenoszone do generacji 2.</span><span class="sxs-lookup"><span data-stu-id="b4837-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="b4837-119">Korzystanie z generacji oznacza, że moduł zbierający elementy bezużyteczne musi pracować tylko podzbiór przydzielone obiekty w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="b4837-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="b4837-120">`COR_PRF_GC_GENERATION` Wyliczenie jest używane przez [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="b4837-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4837-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4837-121">Requirements</span></span>  
 <span data-ttu-id="b4837-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4837-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4837-123">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4837-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4837-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4837-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4837-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4837-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4837-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4837-126">See also</span></span>

- [<span data-ttu-id="b4837-127">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b4837-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
