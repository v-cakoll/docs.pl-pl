---
title: "ICLRControl — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl
helpviewer_keywords: ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98b41ea0062534d9e990a7fe366e8f746ae87f38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="ccea9-102">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-102">ICLRControl Interface</span></span>
<span data-ttu-id="ccea9-103">Udostępnia metody, które umożliwiają hosta można pobrać odwołań do i skonfigurować aspekty środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ccea9-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccea9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ccea9-104">Methods</span></span>  
  
|<span data-ttu-id="ccea9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ccea9-105">Method</span></span>|<span data-ttu-id="ccea9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ccea9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccea9-107">GetCLRManager — metoda</span><span class="sxs-lookup"><span data-stu-id="ccea9-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="ccea9-108">Pobiera wskaźnika interfejsu do wystąpienia dowolnego typu menedżera, która hosta można użyć do skonfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ccea9-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="ccea9-109">SetAppDomainManagerType — metoda</span><span class="sxs-lookup"><span data-stu-id="ccea9-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="ccea9-110">Ustawia typ pochodny typu <xref:System.AppDomainManager> jako typ menedżerom domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ccea9-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccea9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccea9-111">Requirements</span></span>  
 <span data-ttu-id="ccea9-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccea9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccea9-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ccea9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccea9-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccea9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccea9-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccea9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccea9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccea9-116">See Also</span></span>  
 [<span data-ttu-id="ccea9-117">ICLRAssemblyIdentityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ccea9-118">ICLRDebugManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="ccea9-119">ICLRGCManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="ccea9-120">ICLRHostBindingPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="ccea9-121">ICLRHostProtectionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="ccea9-122">ICLROnEventManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="ccea9-123">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="ccea9-124">IHostControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="ccea9-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="ccea9-125">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="ccea9-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
