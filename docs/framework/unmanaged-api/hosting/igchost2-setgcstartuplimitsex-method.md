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
ms.openlocfilehash: f61f6ed5712f3c98f06f5fa76657f3fa7b70fe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666335"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="6461f-102">IGCHost2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="6461f-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="6461f-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="6461f-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6461f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6461f-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6461f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6461f-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="6461f-106">[in] Rozmiar segmentu używaną przez system kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="6461f-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="6461f-107">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="6461f-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6461f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6461f-108">Remarks</span></span>  
 <span data-ttu-id="6461f-109">Wartości, `SetGCStartupLimitsEx` zestawy można określić tylko, aby uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="6461f-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="6461f-110">Te wartości nie można zmienić później.</span><span class="sxs-lookup"><span data-stu-id="6461f-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6461f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6461f-111">Requirements</span></span>  
 <span data-ttu-id="6461f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6461f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6461f-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="6461f-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6461f-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6461f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6461f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6461f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6461f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6461f-116">See also</span></span>
- [<span data-ttu-id="6461f-117">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6461f-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
