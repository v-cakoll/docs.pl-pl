---
title: IGCHost2 — Interfejs
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 43c16415c91521194e0d88be84dd176c3fdadad1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134834"
---
# <a name="igchost2-interface"></a><span data-ttu-id="97851-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="97851-102">IGCHost2 Interface</span></span>
<span data-ttu-id="97851-103">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="97851-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97851-104">W przypadku nowych rozwiązań zalecamy użycie interfejsu [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="97851-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97851-105">Metody</span><span class="sxs-lookup"><span data-stu-id="97851-105">Methods</span></span>  
  
|<span data-ttu-id="97851-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="97851-106">Method</span></span>|<span data-ttu-id="97851-107">Opis</span><span class="sxs-lookup"><span data-stu-id="97851-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97851-108">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="97851-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="97851-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="97851-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="97851-110">Włącza wartość generacji 0 i rozmiary segmentów większe niż `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="97851-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97851-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97851-111">Requirements</span></span>  
 <span data-ttu-id="97851-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97851-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97851-113">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="97851-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="97851-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="97851-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97851-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97851-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97851-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97851-116">See also</span></span>

- [<span data-ttu-id="97851-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="97851-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="97851-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="97851-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="97851-119">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="97851-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
