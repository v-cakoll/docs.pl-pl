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
ms.openlocfilehash: 365261883f0b81884bb7cf70614628c05f9067c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221010"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="ab9a7-102">IGCHost::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab9a7-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="ab9a7-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="ab9a7-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab9a7-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można ustawić rozmiar segmentu i rozmiar maksymalny generacji 0 do wartości większej niż `DWORD` przy użyciu [igchost2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ab9a7-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9a7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab9a7-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab9a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab9a7-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="ab9a7-107">[in] Rozmiar segmentu używaną przez system kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="ab9a7-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="ab9a7-108">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="ab9a7-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab9a7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab9a7-109">Remarks</span></span>  
 <span data-ttu-id="ab9a7-110">`SetGCStartupLimits` Metoda może być wywoływana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ab9a7-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="ab9a7-111">Te wartości nie można zmienić później.</span><span class="sxs-lookup"><span data-stu-id="ab9a7-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab9a7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab9a7-112">Requirements</span></span>  
 <span data-ttu-id="ab9a7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab9a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab9a7-114">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="ab9a7-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ab9a7-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab9a7-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ab9a7-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ab9a7-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab9a7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab9a7-117">See also</span></span>

- [<span data-ttu-id="ab9a7-118">IGCHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab9a7-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
