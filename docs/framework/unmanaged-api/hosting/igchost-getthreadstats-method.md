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
ms.openlocfilehash: 4a7a2da58e197749d492f24c7a12134508efef57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805232"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="c92dc-102">IGCHost::GetThreadStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="c92dc-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="c92dc-103">Pobiera statystyki poszczególnych wątków na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c92dc-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c92dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c92dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c92dc-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="c92dc-106">podczas Wskaźnik do pliku cookie włókna, który określa wątek, dla którego mają zostać pobrane dane statystyczne.</span><span class="sxs-lookup"><span data-stu-id="c92dc-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="c92dc-107">[in. out] Wskaźnik do struktury [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) , która zawiera statystyki wyrzucania elementów bezużytecznych dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="c92dc-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c92dc-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c92dc-108">Requirements</span></span>  
 <span data-ttu-id="c92dc-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c92dc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c92dc-110">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="c92dc-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c92dc-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c92dc-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c92dc-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c92dc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92dc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c92dc-113">See also</span></span>

- [<span data-ttu-id="c92dc-114">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="c92dc-114">IGCHost Interface</span></span>](igchost-interface.md)
