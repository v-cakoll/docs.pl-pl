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
ms.openlocfilehash: cbe94aa67c9cf9ac587b7fca9f5cbeca4870506b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437212"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="85654-102">IGCHost::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="85654-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="85654-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="85654-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85654-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można ustawić rozmiar segmentu i rozmiar maksymalny generacji 0 do wartości większej niż `DWORD` za pomocą [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="85654-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85654-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="85654-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85654-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="85654-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="85654-107">[in] Rozmiar segmentu używaną przez system kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="85654-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="85654-108">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="85654-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85654-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85654-109">Remarks</span></span>  
 <span data-ttu-id="85654-110">`SetGCStartupLimits` Metoda może być wywołana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="85654-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="85654-111">Nie można później zmienić tych wartości.</span><span class="sxs-lookup"><span data-stu-id="85654-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85654-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85654-112">Requirements</span></span>  
 <span data-ttu-id="85654-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85654-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85654-114">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="85654-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="85654-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85654-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85654-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85654-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85654-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85654-117">See Also</span></span>  
 [<span data-ttu-id="85654-118">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="85654-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
