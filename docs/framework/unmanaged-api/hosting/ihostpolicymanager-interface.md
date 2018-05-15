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
ms.openlocfilehash: 7247dddc2d3313948fe6f49fbaa1440b141c4cf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="e5019-102">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5019-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="e5019-103">Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje środowisko uruchomieniowe języka wspólnego (CLR) w przypadku liczby przerywa przekroczenia limitu czasu lub błędów.</span><span class="sxs-lookup"><span data-stu-id="e5019-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5019-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e5019-104">Methods</span></span>  
  
|<span data-ttu-id="e5019-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e5019-105">Method</span></span>|<span data-ttu-id="e5019-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e5019-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5019-107">OnDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="e5019-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="e5019-108">Powiadamia hosta, który ma mieć domyślne działanie określony przez wywołanie do środowiska CLR [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na wątek przerwania lub <xref:System.AppDomain> zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="e5019-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="e5019-109">OnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="e5019-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="e5019-110">Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji lub odzyskiwanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="e5019-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="e5019-111">OnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="e5019-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="e5019-112">Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="e5019-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5019-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5019-113">Requirements</span></span>  
 <span data-ttu-id="e5019-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5019-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5019-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e5019-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5019-116">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5019-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5019-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5019-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5019-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5019-118">See Also</span></span>  
 [<span data-ttu-id="e5019-119">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e5019-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="e5019-120">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e5019-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="e5019-121">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e5019-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="e5019-122">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5019-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="e5019-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e5019-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
