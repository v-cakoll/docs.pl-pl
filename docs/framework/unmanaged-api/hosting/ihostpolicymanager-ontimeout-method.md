---
title: IHostPolicyManager::OnTimeout — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad1a9bc6b2e5c84f15cf0cf706504f18341f8584
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209180"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="cf9d6-102">IHostPolicyManager::OnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf9d6-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="cf9d6-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma mieć z akcją określoną przez wywołanie [iclrpolicymanager::setactionontimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody w odpowiedzi na przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf9d6-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf9d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf9d6-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="cf9d6-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazujący rodzaj operacji, który upłynął limit czasu.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="cf9d6-107">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję CLR trwa w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf9d6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cf9d6-108">Return Value</span></span>  
  
|<span data-ttu-id="cf9d6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf9d6-109">HRESULT</span></span>|<span data-ttu-id="cf9d6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cf9d6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf9d6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf9d6-111">S_OK</span></span>|`OnTimeout` <span data-ttu-id="cf9d6-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-112">returned successfully.</span></span>|  
|<span data-ttu-id="cf9d6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf9d6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf9d6-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cf9d6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cf9d6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cf9d6-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-116">The call timed out.</span></span>|  
|<span data-ttu-id="cf9d6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cf9d6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cf9d6-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cf9d6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cf9d6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cf9d6-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cf9d6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf9d6-121">E_FAIL</span></span>|<span data-ttu-id="cf9d6-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cf9d6-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cf9d6-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cf9d6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf9d6-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf9d6-125">Requirements</span></span>  
 <span data-ttu-id="cf9d6-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf9d6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9d6-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf9d6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf9d6-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf9d6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cf9d6-129">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cf9d6-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf9d6-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf9d6-130">See also</span></span>

- [<span data-ttu-id="cf9d6-131">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cf9d6-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="cf9d6-132">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cf9d6-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="cf9d6-133">ICLRPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cf9d6-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="cf9d6-134">IHostPolicyManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cf9d6-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
