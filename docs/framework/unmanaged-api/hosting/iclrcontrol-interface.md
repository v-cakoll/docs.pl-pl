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
ms.openlocfilehash: 61f9448735f5d26d122ed44c4f41c4fd2a9f7478
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614305"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="8a00d-102">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-102">ICLRControl Interface</span></span>
<span data-ttu-id="8a00d-103">Udostępnia metody, które umożliwia pobieranie odwołań do hosta i Konfiguruj aspekty, środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="8a00d-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a00d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8a00d-104">Methods</span></span>  
  
|<span data-ttu-id="8a00d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8a00d-105">Method</span></span>|<span data-ttu-id="8a00d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8a00d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a00d-107">GetCLRManager, metoda</span><span class="sxs-lookup"><span data-stu-id="8a00d-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="8a00d-108">Pobiera wskaźnik interfejsu do wystąpienia dowolnego typu menedżera, która hosta można użyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8a00d-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="8a00d-109">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="8a00d-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="8a00d-110">Ustawia typ pochodzący od <xref:System.AppDomainManager> jako typ dla menedżerów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a00d-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a00d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a00d-111">Requirements</span></span>  
 <span data-ttu-id="8a00d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a00d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a00d-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a00d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a00d-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a00d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a00d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a00d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a00d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a00d-116">See also</span></span>
- [<span data-ttu-id="8a00d-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8a00d-118">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="8a00d-119">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="8a00d-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="8a00d-121">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="8a00d-122">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="8a00d-123">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="8a00d-124">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a00d-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="8a00d-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8a00d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
