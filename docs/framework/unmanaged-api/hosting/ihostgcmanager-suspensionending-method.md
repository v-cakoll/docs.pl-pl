---
title: IHostGCManager::SuspensionEnding — Metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f65f924b872195000f73bf29b267d1fc30b74f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937728"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="097c7-102">IHostGCManager::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="097c7-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="097c7-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wznawia wykonywanie zadań w wątkach, które zostały zawieszone na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="097c7-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="097c7-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="097c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="097c7-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="097c7-106">podczas Trwa kończenie generowania wyrzucania elementów bezużytecznych, z którego zostanie wznowiony wątek.</span><span class="sxs-lookup"><span data-stu-id="097c7-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="097c7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="097c7-107">Return Value</span></span>  
  
|<span data-ttu-id="097c7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="097c7-108">HRESULT</span></span>|<span data-ttu-id="097c7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="097c7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="097c7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="097c7-110">S_OK</span></span>|<span data-ttu-id="097c7-111">`SuspensionEnding`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="097c7-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="097c7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="097c7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="097c7-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="097c7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="097c7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="097c7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="097c7-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="097c7-115">The call timed out.</span></span>|  
|<span data-ttu-id="097c7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="097c7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="097c7-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="097c7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="097c7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="097c7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="097c7-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="097c7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="097c7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="097c7-120">E_FAIL</span></span>|<span data-ttu-id="097c7-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="097c7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="097c7-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="097c7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="097c7-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="097c7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="097c7-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="097c7-124">Remarks</span></span>  
 <span data-ttu-id="097c7-125">Program CLR wywołuje `SuspensionEnding` po wykonaniu wyrzucania elementów bezużytecznych, aby poinformować hosta, że wątek wznawia wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="097c7-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="097c7-126">Nie należy ponownie zaplanować wątku, z którego wykonano wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="097c7-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="097c7-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="097c7-127">Requirements</span></span>  
 <span data-ttu-id="097c7-128">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="097c7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="097c7-129">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="097c7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="097c7-130">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="097c7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="097c7-131">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="097c7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097c7-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="097c7-132">See also</span></span>

- [<span data-ttu-id="097c7-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c7-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="097c7-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c7-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="097c7-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c7-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="097c7-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c7-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="097c7-137">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c7-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
