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
ms.openlocfilehash: 24a386fe82bbd004954924a573c090af7f58824a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431831"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="7cedf-102">COR_GC_THREAD_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="7cedf-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="7cedf-103">Zawiera dla każdego wątku statystyki dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7cedf-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cedf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cedf-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="7cedf-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7cedf-105">Members</span></span>  
  
|<span data-ttu-id="7cedf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7cedf-106">Member</span></span>|<span data-ttu-id="7cedf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7cedf-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="7cedf-108">Liczba bajtów pamięci przydzielonej w wątku, który jest skojarzony z bieżącym `COR_GC_THREAD_STATS` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7cedf-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="7cedf-109">Ta liczba jest ustawiony na wartość 0 zawsze, gdy występuje zero generowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7cedf-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="7cedf-110">Liczba bajtów podwyższony do wyższych generacji najbardziej aktualnych wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7cedf-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cedf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cedf-111">Remarks</span></span>  
 <span data-ttu-id="7cedf-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="7cedf-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cedf-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cedf-113">Requirements</span></span>  
 <span data-ttu-id="7cedf-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cedf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cedf-115">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="7cedf-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="7cedf-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cedf-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cedf-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cedf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cedf-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cedf-118">See Also</span></span>  
 [<span data-ttu-id="7cedf-119">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="7cedf-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="7cedf-120">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="7cedf-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
