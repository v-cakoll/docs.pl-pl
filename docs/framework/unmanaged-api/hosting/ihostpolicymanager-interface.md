---
title: "IHostPolicyManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0efbc0c51121156d112c63ba4ae59c6c9e95cd95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="30808-102">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="30808-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="30808-103">Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje środowisko uruchomieniowe języka wspólnego (CLR) w przypadku liczby przerywa przekroczenia limitu czasu lub błędów.</span><span class="sxs-lookup"><span data-stu-id="30808-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30808-104">Metody</span><span class="sxs-lookup"><span data-stu-id="30808-104">Methods</span></span>  
  
|<span data-ttu-id="30808-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="30808-105">Method</span></span>|<span data-ttu-id="30808-106">Opis</span><span class="sxs-lookup"><span data-stu-id="30808-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30808-107">OnDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="30808-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="30808-108">Powiadamia hosta, który ma mieć domyślne działanie określony przez wywołanie do środowiska CLR [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na wątek przerwania lub <xref:System.AppDomain> zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="30808-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="30808-109">OnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="30808-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="30808-110">Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji lub odzyskiwanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="30808-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="30808-111">OnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="30808-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="30808-112">Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="30808-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30808-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30808-113">Requirements</span></span>  
 <span data-ttu-id="30808-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30808-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30808-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30808-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30808-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30808-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30808-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30808-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30808-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30808-118">See Also</span></span>  
 [<span data-ttu-id="30808-119">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="30808-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="30808-120">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="30808-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="30808-121">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="30808-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="30808-122">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="30808-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="30808-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="30808-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
