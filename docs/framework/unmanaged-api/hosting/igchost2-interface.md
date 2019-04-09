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
ms.openlocfilehash: 75bef91eb70c8109653741452362cd2e85f625ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138141"
---
# <a name="igchost2-interface"></a><span data-ttu-id="0a6fb-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0a6fb-102">IGCHost2 Interface</span></span>
<span data-ttu-id="0a6fb-103">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0a6fb-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a6fb-104">W nowych wdrożeniach zaleca się, że używasz [iclrgcmanager2 —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) zamiast tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0a6fb-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a6fb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0a6fb-105">Methods</span></span>  
  
|<span data-ttu-id="0a6fb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a6fb-106">Method</span></span>|<span data-ttu-id="0a6fb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0a6fb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a6fb-108">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="0a6fb-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="0a6fb-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="0a6fb-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="0a6fb-110">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="0a6fb-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a6fb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a6fb-111">Requirements</span></span>  
 <span data-ttu-id="0a6fb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a6fb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a6fb-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="0a6fb-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="0a6fb-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a6fb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0a6fb-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0a6fb-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a6fb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a6fb-116">See also</span></span>

- [<span data-ttu-id="0a6fb-117">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="0a6fb-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0a6fb-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="0a6fb-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="0a6fb-119">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="0a6fb-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
