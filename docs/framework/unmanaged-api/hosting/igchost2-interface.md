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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21ce9cbd007858c0f39e12622eff819154ab83f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928614"
---
# <a name="igchost2-interface"></a><span data-ttu-id="78c78-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="78c78-102">IGCHost2 Interface</span></span>
<span data-ttu-id="78c78-103">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="78c78-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78c78-104">W przypadku nowych rozwiązań zalecamy użycie interfejsu [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="78c78-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78c78-105">Metody</span><span class="sxs-lookup"><span data-stu-id="78c78-105">Methods</span></span>  
  
|<span data-ttu-id="78c78-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="78c78-106">Method</span></span>|<span data-ttu-id="78c78-107">Opis</span><span class="sxs-lookup"><span data-stu-id="78c78-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78c78-108">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="78c78-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="78c78-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="78c78-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="78c78-110">Włącza wartość generacji 0 i rozmiary segmentów `DWORD`większe niż.</span><span class="sxs-lookup"><span data-stu-id="78c78-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78c78-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78c78-111">Requirements</span></span>  
 <span data-ttu-id="78c78-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c78-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c78-113">**Nagłówki** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="78c78-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="78c78-114">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="78c78-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78c78-115">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c78-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c78-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78c78-116">See also</span></span>

- [<span data-ttu-id="78c78-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="78c78-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="78c78-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="78c78-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="78c78-119">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="78c78-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
