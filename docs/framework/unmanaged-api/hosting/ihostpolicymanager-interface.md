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
ms.openlocfilehash: d6b34403a45cc40863d79b59396041e496989045
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503942"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="e48f3-102">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e48f3-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="e48f3-103">Dostarcza metody, które powiadamiają hosta o akcjach wykonywanych przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku przerwań, limitów czasu lub niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="e48f3-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e48f3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e48f3-104">Methods</span></span>  
  
|<span data-ttu-id="e48f3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e48f3-105">Method</span></span>|<span data-ttu-id="e48f3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e48f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e48f3-107">OnDefaultAction, metoda</span><span class="sxs-lookup"><span data-stu-id="e48f3-107">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="e48f3-108">Powiadamia hosta, że środowisko CLR ma wykonać akcję domyślną określoną przez wywołanie [ICLRPolicyManager:: SetDefaultAction —](iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na przerwanie lub <xref:System.AppDomain> zwolnienie wątku.</span><span class="sxs-lookup"><span data-stu-id="e48f3-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="e48f3-109">OnFailure, metoda</span><span class="sxs-lookup"><span data-stu-id="e48f3-109">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="e48f3-110">Powiadamia hosta, że środowisko CLR ma wykonać akcję określoną przez wywołanie [ICLRPolicyManager:: SetActionOnFailure —](iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji zasobów lub odzyskania.</span><span class="sxs-lookup"><span data-stu-id="e48f3-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="e48f3-111">OnTimeout, metoda</span><span class="sxs-lookup"><span data-stu-id="e48f3-111">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="e48f3-112">Powiadamia hosta, że środowisko CLR ma wykonać akcję określoną przez wywołanie [ICLRPolicyManager:: SetActionOnTimeout —](iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="e48f3-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e48f3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e48f3-113">Requirements</span></span>  
 <span data-ttu-id="e48f3-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48f3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48f3-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e48f3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e48f3-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e48f3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e48f3-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48f3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e48f3-118">See also</span></span>

- [<span data-ttu-id="e48f3-119">EClrFailure — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e48f3-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="e48f3-120">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e48f3-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="e48f3-121">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e48f3-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="e48f3-122">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e48f3-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="e48f3-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e48f3-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
