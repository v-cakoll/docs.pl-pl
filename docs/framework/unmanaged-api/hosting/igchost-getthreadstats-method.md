---
title: IGCHost::GetThreadStats — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c3d71c75527daa9a9c130d5aaa0d6838816c276
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559427"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="78d7f-102">IGCHost::GetThreadStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="78d7f-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="78d7f-103">Pobiera statystyki wątku wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="78d7f-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78d7f-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78d7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78d7f-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="78d7f-106">[in] Wskaźnik do pliku cookie fiber, określający wątku, do których chcesz pobrać statystyk.</span><span class="sxs-lookup"><span data-stu-id="78d7f-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="78d7f-107">[out w] Wskaźnik do [cor_gc_thread_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) strukturę, która zawiera dane statystyczne kolekcji wyrzucania elementów dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="78d7f-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78d7f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78d7f-108">Requirements</span></span>  
 <span data-ttu-id="78d7f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78d7f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78d7f-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="78d7f-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="78d7f-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78d7f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78d7f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78d7f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d7f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78d7f-113">See also</span></span>
- [<span data-ttu-id="78d7f-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="78d7f-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
