---
title: IGCHost::SetGCStartupLimits — Metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87ba947b9564f82f8daf8cd2ba0acac5cc3587ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928666"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="4703c-102">IGCHost::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="4703c-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="4703c-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="4703c-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4703c-104">Począwszy od .NET Framework 4,5, można ustawić rozmiar segmentu i rozmiar maksymalnej generacji 0 na wartości większe niż `DWORD` przy użyciu metody [IGCHost2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4703c-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4703c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4703c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4703c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4703c-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="4703c-107">podczas Rozmiar segmentu używany przez system odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="4703c-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="4703c-108">podczas Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="4703c-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4703c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4703c-109">Remarks</span></span>  
 <span data-ttu-id="4703c-110">`SetGCStartupLimits` Metoda może być wywoływana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4703c-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="4703c-111">Tych wartości nie można później zmienić.</span><span class="sxs-lookup"><span data-stu-id="4703c-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4703c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4703c-112">Requirements</span></span>  
 <span data-ttu-id="4703c-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4703c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4703c-114">**Nagłówki** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="4703c-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="4703c-115">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4703c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4703c-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4703c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4703c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4703c-117">See also</span></span>

- [<span data-ttu-id="4703c-118">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4703c-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
