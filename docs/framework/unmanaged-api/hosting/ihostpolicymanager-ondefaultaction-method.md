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
ms.openlocfilehash: cdf0a720ac440d156b5b8bdc8dc2c78d3bb5ba86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128560"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="bccd6-102">IHostPolicyManager::OnDefaultAction — Metoda</span><span class="sxs-lookup"><span data-stu-id="bccd6-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="bccd6-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma wykonać akcję domyślną ustawioną przez wywołanie metody [ICLRPolicyManager:: SetDefaultAction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na przerwanie wątku lub <xref:System.AppDomain> Unload.</span><span class="sxs-lookup"><span data-stu-id="bccd6-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bccd6-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bccd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bccd6-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="bccd6-106">podczas Jedna z wartości [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , wskazując rodzaj zdarzenia, do którego odpowiada środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="bccd6-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="bccd6-107">podczas Jedna z wartości [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , wskazująca na akcję, którą wykonuje środowisko CLR w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bccd6-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bccd6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bccd6-108">Return Value</span></span>  
  
|<span data-ttu-id="bccd6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bccd6-109">HRESULT</span></span>|<span data-ttu-id="bccd6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bccd6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bccd6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bccd6-111">S_OK</span></span>|<span data-ttu-id="bccd6-112">`OnDefaultAction` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bccd6-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="bccd6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bccd6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bccd6-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="bccd6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="bccd6-115">została</span><span class="sxs-lookup"><span data-stu-id="bccd6-115">successfully</span></span>|  
|<span data-ttu-id="bccd6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bccd6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bccd6-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="bccd6-117">The call timed out.</span></span>|  
|<span data-ttu-id="bccd6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bccd6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bccd6-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="bccd6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bccd6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bccd6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bccd6-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="bccd6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bccd6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bccd6-122">E_FAIL</span></span>|<span data-ttu-id="bccd6-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bccd6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bccd6-124">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="bccd6-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bccd6-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bccd6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bccd6-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bccd6-126">Requirements</span></span>  
 <span data-ttu-id="bccd6-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bccd6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccd6-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bccd6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bccd6-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bccd6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bccd6-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccd6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccd6-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bccd6-131">See also</span></span>

- [<span data-ttu-id="bccd6-132">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bccd6-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="bccd6-133">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bccd6-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="bccd6-134">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bccd6-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="bccd6-135">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bccd6-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
