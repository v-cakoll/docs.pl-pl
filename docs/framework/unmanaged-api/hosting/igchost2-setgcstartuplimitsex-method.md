---
title: IGCHost2::SetGCStartupLimitsEx — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5e90055a08227ea7cb7fa1b459fe6f5f3a81fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127338"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="c7bd9-102">IGCHost2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7bd9-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="c7bd9-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="c7bd9-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7bd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7bd9-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7bd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7bd9-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="c7bd9-106">[in] Rozmiar segmentu używaną przez system kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="c7bd9-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="c7bd9-107">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="c7bd9-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7bd9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7bd9-108">Remarks</span></span>  
 <span data-ttu-id="c7bd9-109">Wartości, `SetGCStartupLimitsEx` zestawy można określić tylko, aby uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="c7bd9-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="c7bd9-110">Te wartości nie można zmienić później.</span><span class="sxs-lookup"><span data-stu-id="c7bd9-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7bd9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7bd9-111">Requirements</span></span>  
 <span data-ttu-id="c7bd9-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7bd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7bd9-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c7bd9-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c7bd9-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7bd9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7bd9-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7bd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7bd9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7bd9-116">See also</span></span>

- [<span data-ttu-id="c7bd9-117">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7bd9-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
