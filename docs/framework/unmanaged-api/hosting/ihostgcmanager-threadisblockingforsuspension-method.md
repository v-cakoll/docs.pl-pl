---
title: IHostGCManager::ThreadIsBlockingForSuspension — Metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d338b03247f1304f065afc459eb70aac725937c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709809"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="789dc-102">IHostGCManager::ThreadIsBlockingForSuspension — Metoda</span><span class="sxs-lookup"><span data-stu-id="789dc-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="789dc-103">Powiadamia hosta, który jest wątek, z którego wykonano wywołania metody które zamierzasz zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="789dc-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="789dc-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="789dc-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="789dc-105">Return Value</span></span>  
  
|<span data-ttu-id="789dc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="789dc-106">HRESULT</span></span>|<span data-ttu-id="789dc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="789dc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="789dc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="789dc-108">S_OK</span></span>|<span data-ttu-id="789dc-109">`ThreadIsBlockingForSuspension` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="789dc-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="789dc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="789dc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="789dc-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="789dc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="789dc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="789dc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="789dc-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="789dc-113">The call timed out.</span></span>|  
|<span data-ttu-id="789dc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="789dc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="789dc-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="789dc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="789dc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="789dc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="789dc-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="789dc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="789dc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="789dc-118">E_FAIL</span></span>|<span data-ttu-id="789dc-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="789dc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="789dc-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="789dc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="789dc-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="789dc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="789dc-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="789dc-122">Remarks</span></span>  
 <span data-ttu-id="789dc-123">Środowisko CLR jest zazwyczaj wywołuje `ThreadIsBlockForSuspension` metody w ramach przygotowania do wyrzucania elementów bezużytecznych, aby umożliwić hosta ponownie zaplanować wątku dla zadania niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="789dc-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="789dc-124">Host może zmienić harmonogram zadań jedynie po wywołaniu `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="789dc-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="789dc-125">Po środowisko uruchomieniowe wywołuje [suspensionstarting —](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), host nie ponowne planowanie zadania.</span><span class="sxs-lookup"><span data-stu-id="789dc-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="789dc-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="789dc-126">Requirements</span></span>  
 <span data-ttu-id="789dc-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="789dc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="789dc-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="789dc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="789dc-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="789dc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="789dc-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="789dc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789dc-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="789dc-131">See also</span></span>
- [<span data-ttu-id="789dc-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="789dc-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="789dc-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="789dc-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="789dc-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="789dc-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="789dc-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="789dc-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="789dc-136">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="789dc-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
