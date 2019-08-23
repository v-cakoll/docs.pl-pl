---
title: IHostGCManager::SuspensionStarting — Metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3e808c7ed03d7b4cc9dfe77389df6b2eff491f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937722"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="134b0-102">IHostGCManager::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="134b0-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="134b0-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje wykonywanie zadań, aby wykonać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="134b0-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="134b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="134b0-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="134b0-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="134b0-105">Return Value</span></span>  
  
|<span data-ttu-id="134b0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="134b0-106">HRESULT</span></span>|<span data-ttu-id="134b0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="134b0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="134b0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="134b0-108">S_OK</span></span>|<span data-ttu-id="134b0-109">`SuspensionStarting`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="134b0-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="134b0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="134b0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="134b0-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="134b0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="134b0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="134b0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="134b0-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="134b0-113">The call timed out.</span></span>|  
|<span data-ttu-id="134b0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="134b0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="134b0-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="134b0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="134b0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="134b0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="134b0-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="134b0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="134b0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="134b0-118">E_FAIL</span></span>|<span data-ttu-id="134b0-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="134b0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="134b0-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="134b0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="134b0-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="134b0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="134b0-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="134b0-122">Remarks</span></span>  
 <span data-ttu-id="134b0-123">Środowisko CLR wywołuje `SuspensionStarting` , aby poinformować hosta, że występuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="134b0-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="134b0-124">Nie należy ponownie zaplanować tego zadania.</span><span class="sxs-lookup"><span data-stu-id="134b0-124">Do not reschedule this task.</span></span> <span data-ttu-id="134b0-125">Host musi ponownie zaplanować zadanie, gdy zostanie wywołane [ThreadIsBlockingForSuspension —](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) .</span><span class="sxs-lookup"><span data-stu-id="134b0-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="134b0-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="134b0-126">Requirements</span></span>  
 <span data-ttu-id="134b0-127">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="134b0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="134b0-128">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="134b0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="134b0-129">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="134b0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="134b0-130">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="134b0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134b0-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="134b0-131">See also</span></span>

- [<span data-ttu-id="134b0-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="134b0-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="134b0-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="134b0-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="134b0-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="134b0-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="134b0-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="134b0-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="134b0-136">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="134b0-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
