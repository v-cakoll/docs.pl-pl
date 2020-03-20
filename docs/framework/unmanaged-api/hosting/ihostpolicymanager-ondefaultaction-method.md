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
ms.openlocfilehash: 8d987614c1a5a2c90ccb3faa11c605767ae5cfda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178022"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="3c849-102">IHostPolicyManager::OnDefaultAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c849-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="3c849-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma zamiar podjąć domyślną akcję, która została ustawiona przez wywołanie [do metody ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metody w odpowiedzi na przerwanie wątku lub <xref:System.AppDomain> zwolnić.</span><span class="sxs-lookup"><span data-stu-id="3c849-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c849-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c849-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c849-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c849-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3c849-106">[w] Jedna z [wartości EClrOperation,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wskazująca rodzaj zdarzenia, na które odpowiada clr.</span><span class="sxs-lookup"><span data-stu-id="3c849-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="3c849-107">[w] Jedna z wartości [EPolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wskazująca akcję, którą clr podejmuje w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="3c849-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c849-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c849-108">Return Value</span></span>  
  
|<span data-ttu-id="3c849-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c849-109">HRESULT</span></span>|<span data-ttu-id="3c849-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3c849-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c849-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c849-111">S_OK</span></span>|<span data-ttu-id="3c849-112">`OnDefaultAction`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3c849-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="3c849-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c849-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c849-114">Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub przetworzyć wywołanie.</span><span class="sxs-lookup"><span data-stu-id="3c849-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="3c849-115">Pomyślnie</span><span class="sxs-lookup"><span data-stu-id="3c849-115">successfully</span></span>|  
|<span data-ttu-id="3c849-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c849-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c849-117">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="3c849-117">The call timed out.</span></span>|  
|<span data-ttu-id="3c849-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c849-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c849-119">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3c849-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c849-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c849-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c849-121">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="3c849-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c849-122">E_fail</span><span class="sxs-lookup"><span data-stu-id="3c849-122">E_FAIL</span></span>|<span data-ttu-id="3c849-123">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="3c849-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c849-124">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3c849-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c849-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3c849-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c849-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c849-126">Requirements</span></span>  
 <span data-ttu-id="3c849-127">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c849-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c849-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c849-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c849-129">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c849-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c849-130">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c849-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c849-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c849-131">See also</span></span>

- [<span data-ttu-id="3c849-132">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3c849-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="3c849-133">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3c849-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="3c849-134">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c849-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="3c849-135">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c849-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
