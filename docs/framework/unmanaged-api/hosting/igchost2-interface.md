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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138141"
---
# <a name="igchost2-interface"></a><span data-ttu-id="dbd09-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dbd09-102">IGCHost2 Interface</span></span>
<span data-ttu-id="dbd09-103">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dbd09-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbd09-104">W nowych wdrożeniach zaleca się, że używasz [iclrgcmanager2 —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) zamiast tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dbd09-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbd09-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dbd09-105">Methods</span></span>  
  
|<span data-ttu-id="dbd09-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="dbd09-106">Method</span></span>|<span data-ttu-id="dbd09-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dbd09-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbd09-108">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="dbd09-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="dbd09-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="dbd09-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="dbd09-110">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="dbd09-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbd09-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbd09-111">Requirements</span></span>  
 <span data-ttu-id="dbd09-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbd09-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbd09-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="dbd09-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="dbd09-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbd09-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbd09-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbd09-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd09-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbd09-116">See also</span></span>

- [<span data-ttu-id="dbd09-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="dbd09-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="dbd09-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dbd09-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="dbd09-119">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="dbd09-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
