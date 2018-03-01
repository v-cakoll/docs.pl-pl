---
title: "COR_GC_STAT_TYPES — Wyliczenie"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="84adf-102">COR_GC_STAT_TYPES — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="84adf-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="84adf-103">Określa statystyki mają być rejestrowane dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="84adf-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84adf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84adf-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="84adf-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84adf-105">Remarks</span></span>  
 <span data-ttu-id="84adf-106">To wyliczenie Określa, które statystyki w [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury mają być tworzone [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="84adf-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="84adf-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="84adf-107">Members</span></span>  
  
|<span data-ttu-id="84adf-108">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="84adf-108">Member</span></span>|<span data-ttu-id="84adf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="84adf-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="84adf-110">Rejestruje liczbę wyrzucania wykonana w przypadku każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="84adf-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="84adf-111">Rejestruje użycie i odzyskiwanie kolekcji rozmiar statystyki pamięci.</span><span class="sxs-lookup"><span data-stu-id="84adf-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84adf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84adf-112">Requirements</span></span>  
 <span data-ttu-id="84adf-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84adf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84adf-114">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="84adf-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="84adf-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84adf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84adf-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84adf-116">See Also</span></span>  
 [<span data-ttu-id="84adf-117">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="84adf-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="84adf-118">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="84adf-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
