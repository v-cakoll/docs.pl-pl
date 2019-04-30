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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e228cfbdade420c4d5248ffd417c6131083ee74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697280"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="41328-102">COR_GC_STAT_TYPES — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="41328-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="41328-103">Określa statystyki, które mają być rejestrowane dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="41328-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41328-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41328-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="41328-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41328-105">Remarks</span></span>  
 <span data-ttu-id="41328-106">To wyliczenie Określa, które statystyki w [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury mają zostać ustawiona przez [iclrgcmanager::getstats —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="41328-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="41328-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="41328-107">Members</span></span>  
  
|<span data-ttu-id="41328-108">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="41328-108">Member</span></span>|<span data-ttu-id="41328-109">Opis</span><span class="sxs-lookup"><span data-stu-id="41328-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="41328-110">Rejestruje liczbę wyrzucania elementów bezużytecznych wykonywane dla każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="41328-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="41328-111">Rekordy użycia i wyrzucania elementów kolekcji rozmiar statystyki pamięci.</span><span class="sxs-lookup"><span data-stu-id="41328-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41328-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41328-112">Requirements</span></span>  
 <span data-ttu-id="41328-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41328-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41328-114">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="41328-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="41328-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41328-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41328-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41328-116">See also</span></span>

- [<span data-ttu-id="41328-117">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="41328-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="41328-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="41328-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
