---
title: ICLRControl — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06c1f4e1fcfe9c9c361a0e0bb2e8722577a13b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432898"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="ac2af-102">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-102">ICLRControl Interface</span></span>
<span data-ttu-id="ac2af-103">Udostępnia metody, które umożliwiają hosta można pobrać odwołań do i skonfigurować aspekty środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ac2af-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac2af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ac2af-104">Methods</span></span>  
  
|<span data-ttu-id="ac2af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac2af-105">Method</span></span>|<span data-ttu-id="ac2af-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ac2af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac2af-107">GetCLRManager, metoda</span><span class="sxs-lookup"><span data-stu-id="ac2af-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="ac2af-108">Pobiera wskaźnika interfejsu do wystąpienia dowolnego typu menedżera, która hosta można użyć do skonfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ac2af-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="ac2af-109">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="ac2af-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="ac2af-110">Ustawia typ pochodny typu <xref:System.AppDomainManager> jako typ menedżerom domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac2af-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac2af-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac2af-111">Requirements</span></span>  
 <span data-ttu-id="ac2af-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac2af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac2af-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac2af-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac2af-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac2af-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac2af-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2af-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac2af-116">See Also</span></span>  
 [<span data-ttu-id="ac2af-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ac2af-118">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="ac2af-119">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="ac2af-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="ac2af-121">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="ac2af-122">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="ac2af-123">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="ac2af-124">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac2af-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="ac2af-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ac2af-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
