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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984350"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="14c7a-102">IHostPolicyManager::OnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="14c7a-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="14c7a-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma mieć z akcją określoną przez wywołanie [iclrpolicymanager::setactionontimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody w odpowiedzi na przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="14c7a-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14c7a-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14c7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14c7a-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="14c7a-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazujący rodzaj operacji, który upłynął limit czasu.</span><span class="sxs-lookup"><span data-stu-id="14c7a-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="14c7a-107">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję CLR trwa w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="14c7a-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14c7a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="14c7a-108">Return Value</span></span>  
  
|<span data-ttu-id="14c7a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14c7a-109">HRESULT</span></span>|<span data-ttu-id="14c7a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="14c7a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14c7a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="14c7a-111">S_OK</span></span>|<span data-ttu-id="14c7a-112">`OnTimeout` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="14c7a-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="14c7a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14c7a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14c7a-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="14c7a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14c7a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14c7a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14c7a-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="14c7a-116">The call timed out.</span></span>|  
|<span data-ttu-id="14c7a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14c7a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14c7a-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="14c7a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14c7a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14c7a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14c7a-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="14c7a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14c7a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14c7a-121">E_FAIL</span></span>|<span data-ttu-id="14c7a-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="14c7a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14c7a-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="14c7a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14c7a-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="14c7a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14c7a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14c7a-125">Requirements</span></span>  
 <span data-ttu-id="14c7a-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14c7a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14c7a-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14c7a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14c7a-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14c7a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14c7a-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14c7a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c7a-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14c7a-130">See also</span></span>

- [<span data-ttu-id="14c7a-131">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="14c7a-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="14c7a-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="14c7a-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="14c7a-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="14c7a-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="14c7a-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="14c7a-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
