---
title: "IGCHost::GetStats — Metoda"
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
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d105b0aed9c47d5e2d8ad664744e6424db63961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="8c5ec-102">IGCHost::GetStats — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c5ec-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="8c5ec-103">Pobiera statystyki dla bieżącego stanu systemu czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c5ec-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c5ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c5ec-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c5ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c5ec-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="8c5ec-106">[w, out] Wskaźnik do [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury zawierającą statystyki dla bieżącego stanu systemu czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c5ec-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c5ec-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c5ec-107">Remarks</span></span>  
 <span data-ttu-id="8c5ec-108">Statystyki można za pomocą systemu inteligentne alokacji systemu kolekcji garbage działania pomocy.</span><span class="sxs-lookup"><span data-stu-id="8c5ec-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="8c5ec-109">Na przykład system alokacji może ustalić, po zapoznaniu się dane statystyczne, którą chce dodać więcej pamięci lub wymusić kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8c5ec-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c5ec-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c5ec-110">Requirements</span></span>  
 <span data-ttu-id="8c5ec-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c5ec-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c5ec-112">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="8c5ec-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8c5ec-113">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c5ec-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c5ec-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c5ec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5ec-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c5ec-115">See Also</span></span>  
 [<span data-ttu-id="8c5ec-116">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c5ec-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
