---
title: "IGCHost::GetThreadStats — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetThreadStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe84dd4d231bacba6792836844058b7256124db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="5a21d-102">IGCHost::GetThreadStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a21d-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="5a21d-103">Pobiera statystyki dla każdego wątku wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5a21d-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a21d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a21d-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a21d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a21d-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="5a21d-106">[in] Wskaźnik do pliku cookie fiber, który określa wątku, dla których mają zostać pobrane dane statystyczne.</span><span class="sxs-lookup"><span data-stu-id="5a21d-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="5a21d-107">[w, out] Wskaźnik do [cor_gc_thread_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) strukturę, która zawiera dane statystyczne kolekcji pamięci dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="5a21d-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a21d-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a21d-108">Requirements</span></span>  
 <span data-ttu-id="5a21d-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a21d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a21d-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="5a21d-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="5a21d-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a21d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a21d-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a21d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a21d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a21d-113">See Also</span></span>  
 [<span data-ttu-id="5a21d-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a21d-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
