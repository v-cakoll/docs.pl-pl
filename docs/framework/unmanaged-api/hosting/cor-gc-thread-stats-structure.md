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
ms.openlocfilehash: 64e0c466edcd8863244e6ed184c18422b5f66875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178267"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="77bea-102">COR_GC_THREAD_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="77bea-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="77bea-103">Zawiera statystyki na wątek odnoszące się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="77bea-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77bea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77bea-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="77bea-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="77bea-105">Members</span></span>  
  
|<span data-ttu-id="77bea-106">Członek</span><span class="sxs-lookup"><span data-stu-id="77bea-106">Member</span></span>|<span data-ttu-id="77bea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="77bea-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="77bea-108">Liczba bajtów pamięci przydzielonej w wątku, który `COR_GC_THREAD_STATS` jest skojarzony z bieżącym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="77bea-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="77bea-109">Ta liczba jest czyszczona do zera za każdym razem, gdy występuje wyrzucanie elementów bezużytecznych z wartością zerową generacji.</span><span class="sxs-lookup"><span data-stu-id="77bea-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="77bea-110">Liczba bajtów promowanych do wyższej generacji w najnowszej wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="77bea-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77bea-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77bea-111">Remarks</span></span>  
 <span data-ttu-id="77bea-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="77bea-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77bea-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77bea-113">Requirements</span></span>  
 <span data-ttu-id="77bea-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77bea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77bea-115">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="77bea-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="77bea-116">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77bea-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77bea-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77bea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77bea-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77bea-118">See also</span></span>

- [<span data-ttu-id="77bea-119">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="77bea-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="77bea-120">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="77bea-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
