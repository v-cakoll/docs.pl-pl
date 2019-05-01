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
ms.openlocfilehash: f70e7958cc9ac198738ed72732fe7b6563c89067
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970069"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="217ef-102">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-102">ICLRControl Interface</span></span>
<span data-ttu-id="217ef-103">Udostępnia metody, które umożliwia pobieranie odwołań do hosta i Konfiguruj aspekty, środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="217ef-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="217ef-104">Metody</span><span class="sxs-lookup"><span data-stu-id="217ef-104">Methods</span></span>  
  
|<span data-ttu-id="217ef-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="217ef-105">Method</span></span>|<span data-ttu-id="217ef-106">Opis</span><span class="sxs-lookup"><span data-stu-id="217ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="217ef-107">GetCLRManager, metoda</span><span class="sxs-lookup"><span data-stu-id="217ef-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="217ef-108">Pobiera wskaźnik interfejsu do wystąpienia dowolnego typu menedżera, która hosta można użyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="217ef-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="217ef-109">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="217ef-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="217ef-110">Ustawia typ pochodzący od <xref:System.AppDomainManager> jako typ dla menedżerów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="217ef-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="217ef-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="217ef-111">Requirements</span></span>  
 <span data-ttu-id="217ef-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="217ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="217ef-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="217ef-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="217ef-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="217ef-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="217ef-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="217ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217ef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="217ef-116">See also</span></span>

- [<span data-ttu-id="217ef-117">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="217ef-118">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="217ef-119">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="217ef-120">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="217ef-121">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="217ef-122">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="217ef-123">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="217ef-124">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="217ef-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="217ef-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="217ef-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
