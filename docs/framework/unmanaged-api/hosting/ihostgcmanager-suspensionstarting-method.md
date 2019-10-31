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
ms.openlocfilehash: bf1b830f55110c00356527bc9caa41dfd94ae377
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130456"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="7c7d1-102">IHostGCManager::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c7d1-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="7c7d1-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje wykonywanie zadań, aby wykonać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c7d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c7d1-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7c7d1-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c7d1-105">Return Value</span></span>  
  
|<span data-ttu-id="7c7d1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c7d1-106">HRESULT</span></span>|<span data-ttu-id="7c7d1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7c7d1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c7d1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c7d1-108">S_OK</span></span>|<span data-ttu-id="7c7d1-109">`SuspensionStarting` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="7c7d1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c7d1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c7d1-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c7d1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c7d1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c7d1-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-113">The call timed out.</span></span>|  
|<span data-ttu-id="7c7d1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c7d1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c7d1-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c7d1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c7d1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c7d1-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c7d1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c7d1-118">E_FAIL</span></span>|<span data-ttu-id="7c7d1-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c7d1-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c7d1-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c7d1-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c7d1-122">Remarks</span></span>  
 <span data-ttu-id="7c7d1-123">Wywołania CLR `SuspensionStarting`, aby poinformować hosta, że występuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7c7d1-124">Nie należy ponownie zaplanować tego zadania.</span><span class="sxs-lookup"><span data-stu-id="7c7d1-124">Do not reschedule this task.</span></span> <span data-ttu-id="7c7d1-125">Host musi ponownie zaplanować zadanie, gdy zostanie wywołane [ThreadIsBlockingForSuspension —](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7c7d1-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c7d1-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c7d1-126">Requirements</span></span>  
 <span data-ttu-id="7c7d1-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c7d1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c7d1-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c7d1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c7d1-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c7d1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c7d1-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c7d1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7d1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c7d1-131">See also</span></span>

- [<span data-ttu-id="7c7d1-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c7d1-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="7c7d1-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c7d1-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="7c7d1-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c7d1-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="7c7d1-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c7d1-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="7c7d1-136">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c7d1-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
