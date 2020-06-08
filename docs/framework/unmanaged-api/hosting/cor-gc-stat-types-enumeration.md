---
title: COR_GC_STAT_TYPES — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501706"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="602af-102">COR_GC_STAT_TYPES — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="602af-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="602af-103">Określa statystyki, które mają być rejestrowane w celu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="602af-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="602af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="602af-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="602af-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="602af-105">Remarks</span></span>  
 <span data-ttu-id="602af-106">To Wyliczenie określa, które statystyki w strukturze [COR_GC_STATS](cor-gc-stats-structure.md) mają być ustawiane za pomocą metody [ICLRGCManager::](iclrgcmanager-getstats-method.md) getstatistics.</span><span class="sxs-lookup"><span data-stu-id="602af-106">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="602af-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="602af-107">Members</span></span>  
  
|<span data-ttu-id="602af-108">Członek</span><span class="sxs-lookup"><span data-stu-id="602af-108">Member</span></span>|<span data-ttu-id="602af-109">Opis</span><span class="sxs-lookup"><span data-stu-id="602af-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="602af-110">Rejestruje liczbę kolekcji elementów bezużytecznych wykonanych dla każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="602af-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="602af-111">Rejestruje dane statystyczne dotyczące użycia pamięci i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="602af-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="602af-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="602af-112">Requirements</span></span>  
 <span data-ttu-id="602af-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="602af-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="602af-114">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="602af-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="602af-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="602af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602af-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="602af-116">See also</span></span>

- [<span data-ttu-id="602af-117">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="602af-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="602af-118">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="602af-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
