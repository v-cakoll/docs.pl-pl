---
title: "COR_GC_THREAD_STATS — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10366d183ed7fd7386609e4c5726df0cea4e29a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="f7833-102">COR_GC_THREAD_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="f7833-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="f7833-103">Zawiera dla każdego wątku statystyki dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f7833-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7833-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7833-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="f7833-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f7833-105">Members</span></span>  
  
|<span data-ttu-id="f7833-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f7833-106">Member</span></span>|<span data-ttu-id="f7833-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f7833-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="f7833-108">Liczba bajtów pamięci przydzielonej w wątku, który jest skojarzony z bieżącym `COR_GC_THREAD_STATS` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f7833-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="f7833-109">Ta liczba jest ustawiony na wartość 0 zawsze, gdy występuje zero generowania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f7833-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="f7833-110">Liczba bajtów podwyższony do wyższych generacji najbardziej aktualnych wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f7833-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7833-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7833-111">Remarks</span></span>  
 <span data-ttu-id="f7833-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="f7833-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7833-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7833-113">Requirements</span></span>  
 <span data-ttu-id="f7833-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7833-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7833-115">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="f7833-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="f7833-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7833-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7833-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7833-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7833-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7833-118">See Also</span></span>  
 [<span data-ttu-id="f7833-119">Hosting — struktury</span><span class="sxs-lookup"><span data-stu-id="f7833-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="f7833-120">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="f7833-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
