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
ms.openlocfilehash: b0fbc462283ef1577de8100e60fd09caa53db539
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131912"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="9788a-102">COR_GC_STAT_TYPES — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9788a-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="9788a-103">Określa statystyki, które mają być rejestrowane w celu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9788a-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9788a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9788a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="9788a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9788a-105">Remarks</span></span>  
 <span data-ttu-id="9788a-106">To Wyliczenie określa, które statystyki w strukturze [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) mają być ustawiane za pomocą metody [ICLRGCManager::](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) getstatistics.</span><span class="sxs-lookup"><span data-stu-id="9788a-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="9788a-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9788a-107">Members</span></span>  
  
|<span data-ttu-id="9788a-108">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9788a-108">Member</span></span>|<span data-ttu-id="9788a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9788a-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="9788a-110">Rejestruje liczbę kolekcji elementów bezużytecznych wykonanych dla każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="9788a-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="9788a-111">Rejestruje dane statystyczne dotyczące użycia pamięci i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9788a-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9788a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9788a-112">Requirements</span></span>  
 <span data-ttu-id="9788a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9788a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9788a-114">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="9788a-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9788a-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9788a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9788a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9788a-116">See also</span></span>

- [<span data-ttu-id="9788a-117">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="9788a-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="9788a-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9788a-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
