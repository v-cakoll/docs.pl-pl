---
title: IHostTaskManager::EndThreadAffinity — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8de8816f08fa98055bb397d77d060721a0fb30d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557919"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="fb61a-102">IHostTaskManager::EndThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb61a-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="fb61a-103">Powiadamia hosta, którego kod zarządzany jest kończone okres, w którym bieżące zadanie musi nie można przenieść na inny wątek systemu operacyjnego, zgodnie z wcześniejszym wywołaniem [ihosttaskmanager::beginthreadaffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="fb61a-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb61a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb61a-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fb61a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fb61a-105">Return Value</span></span>  
  
|<span data-ttu-id="fb61a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb61a-106">HRESULT</span></span>|<span data-ttu-id="fb61a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fb61a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb61a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb61a-108">S_OK</span></span>|<span data-ttu-id="fb61a-109">`EndThreadAffinity` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fb61a-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="fb61a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb61a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb61a-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fb61a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb61a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb61a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb61a-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fb61a-113">The call timed out.</span></span>|  
|<span data-ttu-id="fb61a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb61a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb61a-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="fb61a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb61a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb61a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb61a-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fb61a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb61a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb61a-118">E_FAIL</span></span>|<span data-ttu-id="fb61a-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fb61a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb61a-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fb61a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb61a-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb61a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fb61a-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="fb61a-122">E_UNEXPECTED</span></span>|<span data-ttu-id="fb61a-123">`EndThreadAffinity` Wywołano bez wcześniej odpowiedniego wywołania `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="fb61a-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb61a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb61a-124">Remarks</span></span>  
 <span data-ttu-id="fb61a-125">Środowisko CLR wywołuje odpowiedniego `BeginThreadAffinity` na bieżące zadanie przed wywołaniem `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="fb61a-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="fb61a-126">W przypadku braku takich odpowiedniego wywołania implementacji hosta [ihosttaskmanager —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinien zwrócić wartość E_UNEXPECTED, a nie podejmuj żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="fb61a-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb61a-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb61a-127">Requirements</span></span>  
 <span data-ttu-id="fb61a-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb61a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb61a-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb61a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb61a-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb61a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb61a-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb61a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb61a-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb61a-132">See also</span></span>
- <xref:System.Threading>
- [<span data-ttu-id="fb61a-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb61a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fb61a-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb61a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fb61a-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb61a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fb61a-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb61a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
