---
title: IHostPolicyManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9d903b4e44ea7a185ad8b3b71b7a5da2f2bda3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126350"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="1e033-102">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1e033-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="1e033-103">Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje środowisko uruchomieniowe języka wspólnego (CLR) w przypadku właściwości przerywa przekroczenia limitu czasu lub niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="1e033-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e033-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1e033-104">Methods</span></span>  
  
|<span data-ttu-id="1e033-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e033-105">Method</span></span>|<span data-ttu-id="1e033-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1e033-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e033-107">OnDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="1e033-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="1e033-108">Powiadamia hosta, który ma mieć domyślne działanie określony przez wywołanie do środowiska CLR [iclrpolicymanager::setdefaultaction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na wątek przerwania lub <xref:System.AppDomain> zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="1e033-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="1e033-109">OnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="1e033-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="1e033-110">Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [iclrpolicymanager::setactiononfailure —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji lub odzyskiwanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="1e033-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="1e033-111">OnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="1e033-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="1e033-112">Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [iclrpolicymanager::setactionontimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="1e033-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e033-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1e033-113">Requirements</span></span>  
 <span data-ttu-id="1e033-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e033-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e033-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e033-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e033-116">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e033-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e033-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e033-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e033-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e033-118">See also</span></span>

- [<span data-ttu-id="1e033-119">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1e033-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="1e033-120">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1e033-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="1e033-121">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1e033-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="1e033-122">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1e033-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="1e033-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1e033-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
