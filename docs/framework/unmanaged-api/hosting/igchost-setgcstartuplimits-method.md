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
ms.openlocfilehash: e65a83d1da0580436babd15e4f27e2db7a698668
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377612"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="95627-102">IGCHost::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="95627-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="95627-103">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="95627-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95627-104">Począwszy od programu .NET Framework 4.5, można ustawić rozmiaru maksymalnego generacji 0 i segmentu wartości większej niż `DWORD` przy użyciu [igchost2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="95627-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95627-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="95627-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95627-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="95627-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="95627-107">[in] Rozmiar segmentu używaną przez system kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="95627-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="95627-108">[in] Maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="95627-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95627-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95627-109">Remarks</span></span>  
 <span data-ttu-id="95627-110">`SetGCStartupLimits` Metoda może być wywoływana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="95627-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="95627-111">Te wartości nie można zmienić później.</span><span class="sxs-lookup"><span data-stu-id="95627-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95627-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95627-112">Requirements</span></span>  
 <span data-ttu-id="95627-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95627-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95627-114">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="95627-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="95627-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95627-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95627-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95627-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95627-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95627-117">See also</span></span>

- [<span data-ttu-id="95627-118">IGCHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="95627-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
