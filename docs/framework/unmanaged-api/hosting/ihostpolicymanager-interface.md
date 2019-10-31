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
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128598"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="0e161-102">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0e161-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="0e161-103">Dostarcza metody, które powiadamiają hosta o akcjach wykonywanych przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku przerwań, limitów czasu lub niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="0e161-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e161-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e161-104">Methods</span></span>  
  
|<span data-ttu-id="0e161-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e161-105">Method</span></span>|<span data-ttu-id="0e161-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0e161-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e161-107">OnDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="0e161-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="0e161-108">Powiadamia hosta, że środowisko CLR ma wykonać akcję domyślną określoną przez wywołanie [ICLRPolicyManager:: SetDefaultAction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na przerwanie wątku lub <xref:System.AppDomain> Unload.</span><span class="sxs-lookup"><span data-stu-id="0e161-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="0e161-109">OnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="0e161-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="0e161-110">Powiadamia hosta, że środowisko CLR ma wykonać akcję określoną przez wywołanie [ICLRPolicyManager:: SetActionOnFailure —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji zasobów lub odzyskania.</span><span class="sxs-lookup"><span data-stu-id="0e161-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="0e161-111">OnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="0e161-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="0e161-112">Powiadamia hosta, że środowisko CLR ma wykonać akcję określoną przez wywołanie [ICLRPolicyManager:: SetActionOnTimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="0e161-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e161-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e161-113">Requirements</span></span>  
 <span data-ttu-id="0e161-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e161-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e161-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e161-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e161-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e161-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e161-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e161-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e161-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e161-118">See also</span></span>

- [<span data-ttu-id="0e161-119">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0e161-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="0e161-120">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0e161-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="0e161-121">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0e161-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="0e161-122">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e161-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="0e161-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0e161-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
