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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867218"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="38031-102">COR_PRF_GC_GENERATION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="38031-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="38031-103">Identyfikuje Generowanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="38031-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38031-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38031-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="38031-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="38031-105">Members</span></span>  
  
|<span data-ttu-id="38031-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="38031-106">Member</span></span>|<span data-ttu-id="38031-107">Opis</span><span class="sxs-lookup"><span data-stu-id="38031-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="38031-108">Obiekt jest przechowywany jako generacja 0.</span><span class="sxs-lookup"><span data-stu-id="38031-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="38031-109">Obiekt jest przechowywany jako generacja 1.</span><span class="sxs-lookup"><span data-stu-id="38031-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="38031-110">Obiekt jest przechowywany jako generacja 2.</span><span class="sxs-lookup"><span data-stu-id="38031-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="38031-111">Obiekt jest przechowywany w stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="38031-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38031-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38031-112">Remarks</span></span>  
 <span data-ttu-id="38031-113">Moduł wyrzucania elementów bezużytecznych zwiększa wydajność zarządzania pamięcią, dzieląc obiekty na generacji na podstawie wieku.</span><span class="sxs-lookup"><span data-stu-id="38031-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="38031-114">Moduł wyrzucania elementów bezużytecznych obecnie używa trzech generacji, numerowanych 0, 1 i 2, a także specjalnego segmentu sterty, który jest używany w przypadku dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="38031-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="38031-115">Obiekty, których rozmiar jest większy niż określona wartość, są przechowywane w stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="38031-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="38031-116">Inne przydziały, które zaczynają się od wygenerowania 0.</span><span class="sxs-lookup"><span data-stu-id="38031-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="38031-117">Wszystkie obiekty istniejące po wyrzucaniu elementów bezużytecznych w generacji 0 są podwyższane do generacji 1.</span><span class="sxs-lookup"><span data-stu-id="38031-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="38031-118">Obiekty istniejące po wyrzucaniu elementów bezużytecznych odbywają się w generacji 1.</span><span class="sxs-lookup"><span data-stu-id="38031-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="38031-119">Użycie generacji oznacza, że moduł zbierający elementy bezużyteczne musi współpracować z tylko podzbiorem przyznanych obiektów w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="38031-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="38031-120">Wyliczenie `COR_PRF_GC_GENERATION` jest używane przez strukturę [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="38031-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38031-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38031-121">Requirements</span></span>  
 <span data-ttu-id="38031-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38031-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38031-123">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="38031-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38031-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38031-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38031-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38031-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38031-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38031-126">See also</span></span>

- [<span data-ttu-id="38031-127">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="38031-127">Profiling Enumerations</span></span>](profiling-enumerations.md)
