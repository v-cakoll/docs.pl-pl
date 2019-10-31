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
ms.openlocfilehash: d78f81093e61c40eaec334f957d8583eeb593f5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134815"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="ba9d6-102">IGCHost2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba9d6-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="ba9d6-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="ba9d6-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba9d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba9d6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba9d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba9d6-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="ba9d6-106">podczas Rozmiar segmentu używany przez system odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="ba9d6-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="ba9d6-107">podczas Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="ba9d6-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba9d6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba9d6-108">Remarks</span></span>  
 <span data-ttu-id="ba9d6-109">Wartości, które `SetGCStartupLimitsEx` zestawy, można określić tylko przed uruchomieniem hosta.</span><span class="sxs-lookup"><span data-stu-id="ba9d6-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="ba9d6-110">Tych wartości nie można później zmienić.</span><span class="sxs-lookup"><span data-stu-id="ba9d6-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba9d6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba9d6-111">Requirements</span></span>  
 <span data-ttu-id="ba9d6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba9d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba9d6-113">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="ba9d6-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ba9d6-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba9d6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba9d6-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba9d6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba9d6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba9d6-116">See also</span></span>

- [<span data-ttu-id="ba9d6-117">IGCHost2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba9d6-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
