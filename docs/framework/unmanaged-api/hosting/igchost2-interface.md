---
title: "IGCHost2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2
helpviewer_keywords: IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6706696e3fd5158d2b49a4d114d978a26510b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="igchost2-interface"></a><span data-ttu-id="11881-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="11881-102">IGCHost2 Interface</span></span>
<span data-ttu-id="11881-103">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="11881-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11881-104">W nowych wdrożeniach, firma Microsoft zaleca się używanie [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) zamiast tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="11881-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11881-105">Metody</span><span class="sxs-lookup"><span data-stu-id="11881-105">Methods</span></span>  
  
|<span data-ttu-id="11881-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="11881-106">Method</span></span>|<span data-ttu-id="11881-107">Opis</span><span class="sxs-lookup"><span data-stu-id="11881-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11881-108">SetGCStartupLimitsEx — metoda</span><span class="sxs-lookup"><span data-stu-id="11881-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="11881-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="11881-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="11881-110">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="11881-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11881-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11881-111">Requirements</span></span>  
 <span data-ttu-id="11881-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11881-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11881-113">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="11881-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="11881-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11881-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11881-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11881-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11881-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11881-116">See Also</span></span>  
 [<span data-ttu-id="11881-117">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="11881-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="11881-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="11881-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="11881-119">Corruntimehost — klasa Coclass</span><span class="sxs-lookup"><span data-stu-id="11881-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
