---
title: IHostPolicyManager::OnDefaultAction — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37d04855a7ddc613c3857867179ec84ea0f7b6ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780982"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="80c35-102">IHostPolicyManager::OnDefaultAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="80c35-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="80c35-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma mieć domyślną akcję, która została ustawiona przez wywołanie [iclrpolicymanager::setdefaultaction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metody w odpowiedzi na przerwanie wątku lub <xref:System.AppDomain> zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="80c35-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80c35-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80c35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80c35-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="80c35-106">[in] Jedną z [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości, wskazujący rodzaj zdarzeń, do którego odpowiada środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="80c35-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="80c35-107">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazując akcję, która zajmuje środowisko CLR w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="80c35-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80c35-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80c35-108">Return Value</span></span>  
  
|<span data-ttu-id="80c35-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80c35-109">HRESULT</span></span>|<span data-ttu-id="80c35-110">Opis</span><span class="sxs-lookup"><span data-stu-id="80c35-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80c35-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80c35-111">S_OK</span></span>|<span data-ttu-id="80c35-112">`OnDefaultAction` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="80c35-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="80c35-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80c35-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80c35-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetwarzania wywołania.</span><span class="sxs-lookup"><span data-stu-id="80c35-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="80c35-115">pomyślnie</span><span class="sxs-lookup"><span data-stu-id="80c35-115">successfully</span></span>|  
|<span data-ttu-id="80c35-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80c35-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80c35-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="80c35-117">The call timed out.</span></span>|  
|<span data-ttu-id="80c35-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80c35-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80c35-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="80c35-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80c35-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80c35-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80c35-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="80c35-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80c35-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80c35-122">E_FAIL</span></span>|<span data-ttu-id="80c35-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="80c35-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80c35-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="80c35-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80c35-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="80c35-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80c35-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80c35-126">Requirements</span></span>  
 <span data-ttu-id="80c35-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c35-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c35-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80c35-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80c35-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80c35-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80c35-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c35-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c35-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80c35-131">See also</span></span>

- [<span data-ttu-id="80c35-132">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="80c35-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="80c35-133">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="80c35-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="80c35-134">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="80c35-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="80c35-135">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="80c35-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
