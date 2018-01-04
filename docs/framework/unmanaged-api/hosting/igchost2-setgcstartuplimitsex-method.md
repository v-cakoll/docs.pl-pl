---
title: "IGCHost2::SetGCStartupLimitsEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8ed2b2aa43fcf925b6202ab339209904e7c53af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="9c12a-102">IGCHost2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c12a-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="9c12a-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="9c12a-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c12a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c12a-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c12a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c12a-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="9c12a-106">[in] Rozmiar segmentu używaną przez system kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="9c12a-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="9c12a-107">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="9c12a-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c12a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c12a-108">Remarks</span></span>  
 <span data-ttu-id="9c12a-109">Wartości który `SetGCStartupLimitsEx` zestawy można określić jedynie, aby uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="9c12a-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="9c12a-110">Nie można później zmienić tych wartości.</span><span class="sxs-lookup"><span data-stu-id="9c12a-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c12a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c12a-111">Requirements</span></span>  
 <span data-ttu-id="9c12a-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c12a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c12a-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="9c12a-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9c12a-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c12a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c12a-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c12a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c12a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c12a-116">See Also</span></span>  
 [<span data-ttu-id="9c12a-117">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c12a-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
