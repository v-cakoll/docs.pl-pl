---
title: COR_GC_THREAD_STATS — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a4b56270318a05d0e5a480fdb56eb45593d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177739"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="0cb3e-102">COR_GC_THREAD_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="0cb3e-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="0cb3e-103">Zawiera statystyki wątku odnoszących się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0cb3e-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cb3e-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="0cb3e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0cb3e-105">Members</span></span>  
  
|<span data-ttu-id="0cb3e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0cb3e-106">Member</span></span>|<span data-ttu-id="0cb3e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0cb3e-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="0cb3e-108">Liczba bajtów pamięci przydzielonej na wątek, który jest skojarzony z bieżącym `COR_GC_THREAD_STATS` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0cb3e-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="0cb3e-109">Ta liczba jest ustawiony na wartość 0, każdym razem, gdy występuje zero generacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0cb3e-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="0cb3e-110">Liczba bajtów podwyższony do wyższej generacji najbardziej aktualnych wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0cb3e-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cb3e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cb3e-111">Remarks</span></span>  
 <span data-ttu-id="0cb3e-112">[Iclrtask::getmemstats —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="0cb3e-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb3e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0cb3e-113">Requirements</span></span>  
 <span data-ttu-id="0cb3e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb3e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb3e-115">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="0cb3e-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="0cb3e-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0cb3e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0cb3e-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0cb3e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0cb3e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cb3e-118">See also</span></span>

- [<span data-ttu-id="0cb3e-119">Hosting — Struktury</span><span class="sxs-lookup"><span data-stu-id="0cb3e-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="0cb3e-120">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0cb3e-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
