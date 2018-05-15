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
ms.openlocfilehash: 5c6cbf44bd02a45b9b99d2dad63fc5bd6219c4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="igchost2-interface"></a><span data-ttu-id="b5d73-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b5d73-102">IGCHost2 Interface</span></span>
<span data-ttu-id="b5d73-103">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b5d73-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5d73-104">W nowych wdrożeniach, firma Microsoft zaleca się używanie [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) zamiast tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b5d73-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5d73-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b5d73-105">Methods</span></span>  
  
|<span data-ttu-id="b5d73-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b5d73-106">Method</span></span>|<span data-ttu-id="b5d73-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b5d73-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5d73-108">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="b5d73-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="b5d73-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="b5d73-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="b5d73-110">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="b5d73-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5d73-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5d73-111">Requirements</span></span>  
 <span data-ttu-id="b5d73-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5d73-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5d73-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b5d73-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b5d73-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5d73-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5d73-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5d73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d73-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5d73-116">See Also</span></span>  
 [<span data-ttu-id="b5d73-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b5d73-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b5d73-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b5d73-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="b5d73-119">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="b5d73-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
