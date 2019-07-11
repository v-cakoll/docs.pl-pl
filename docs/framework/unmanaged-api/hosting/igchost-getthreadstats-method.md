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
ms.openlocfilehash: 87e318c4f2367e8c66910978f4a9c89f36c95632
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766507"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="f0994-102">IGCHost::GetThreadStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0994-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="f0994-103">Pobiera statystyki wątku wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f0994-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0994-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0994-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0994-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0994-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="f0994-106">[in] Wskaźnik do pliku cookie fiber, określający wątku, do których chcesz pobrać statystyk.</span><span class="sxs-lookup"><span data-stu-id="f0994-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="f0994-107">[out w] Wskaźnik do [cor_gc_thread_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) strukturę, która zawiera dane statystyczne kolekcji wyrzucania elementów dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f0994-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0994-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0994-108">Requirements</span></span>  
 <span data-ttu-id="f0994-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0994-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0994-110">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f0994-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f0994-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0994-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0994-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0994-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0994-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0994-113">See also</span></span>

- [<span data-ttu-id="f0994-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0994-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
