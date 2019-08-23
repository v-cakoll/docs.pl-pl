---
title: IHostTaskManager::ReverseEnterRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e5beabb5ac1b5a4b2a34ae8e18b7fad7c86504
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959049"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="0ef5a-102">IHostTaskManager::ReverseEnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ef5a-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="0ef5a-103">Powiadamia hosta, że wywołanie jest nawiązywane w środowisku uruchomieniowym języka wspólnego (CLR) z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ef5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ef5a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0ef5a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0ef5a-105">Return Value</span></span>  
  
|<span data-ttu-id="0ef5a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ef5a-106">HRESULT</span></span>|<span data-ttu-id="0ef5a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0ef5a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ef5a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ef5a-108">S_OK</span></span>|<span data-ttu-id="0ef5a-109">`ReverseEnterRuntime`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0ef5a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ef5a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ef5a-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ef5a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ef5a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ef5a-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-113">The call timed out.</span></span>|  
|<span data-ttu-id="0ef5a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ef5a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ef5a-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ef5a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ef5a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ef5a-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ef5a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ef5a-118">E_FAIL</span></span>|<span data-ttu-id="0ef5a-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ef5a-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ef5a-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ef5a-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0ef5a-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0ef5a-123">Za mało dostępnej pamięci, aby zakończyć żądaną alokację zasobów.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ef5a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ef5a-124">Remarks</span></span>  
 <span data-ttu-id="0ef5a-125">Jeśli wywołanie do środowiska CLR zostanie wykonane z sekwencji, która pochodzi z kodu zarządzanego, każde wywołanie `ReverseEnterRuntime` odpowiada wywołaniu [ReverseLeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ef5a-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ef5a-126">Wywołania mogą pochodzić z niezarządzanego kodu bez zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="0ef5a-127">W tym przypadku nie istnieje wywołanie metody [EnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)lub `ReverseLeaveRuntime`, `ReverseEnterRuntime` a liczba wywołań nie jest równa liczbie wywołań do `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="0ef5a-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ef5a-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ef5a-128">Requirements</span></span>  
 <span data-ttu-id="0ef5a-129">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ef5a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ef5a-130">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ef5a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ef5a-131">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0ef5a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ef5a-132">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ef5a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef5a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ef5a-133">See also</span></span>

- [<span data-ttu-id="0ef5a-134">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ef5a-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0ef5a-135">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ef5a-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0ef5a-136">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ef5a-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0ef5a-137">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ef5a-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
