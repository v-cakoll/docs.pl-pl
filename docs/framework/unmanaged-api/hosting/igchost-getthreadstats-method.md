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
ms.openlocfilehash: 36eeb7ed4f80979ef2edb930e65963a1db0c894f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134904"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="abe2e-102">IGCHost::GetThreadStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="abe2e-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="abe2e-103">Pobiera statystyki poszczególnych wątków na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="abe2e-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abe2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abe2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abe2e-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="abe2e-106">podczas Wskaźnik do pliku cookie włókna, który określa wątek, dla którego mają zostać pobrane dane statystyczne.</span><span class="sxs-lookup"><span data-stu-id="abe2e-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="abe2e-107">[in. out] Wskaźnik do struktury [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) , która zawiera statystyki wyrzucania elementów bezużytecznych dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="abe2e-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe2e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abe2e-108">Requirements</span></span>  
 <span data-ttu-id="abe2e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe2e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe2e-110">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="abe2e-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="abe2e-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="abe2e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abe2e-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe2e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe2e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abe2e-113">See also</span></span>

- [<span data-ttu-id="abe2e-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="abe2e-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
