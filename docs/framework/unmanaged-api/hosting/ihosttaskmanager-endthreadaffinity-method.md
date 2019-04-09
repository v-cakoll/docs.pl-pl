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
ms.openlocfilehash: 3f94f365aa8c9221c64e9611deab3597e06ed862
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157901"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="42185-102">IHostTaskManager::EndThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="42185-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="42185-103">Powiadamia hosta, którego kod zarządzany jest kończone okres, w którym bieżące zadanie musi nie można przenieść na inny wątek systemu operacyjnego, zgodnie z wcześniejszym wywołaniem [ihosttaskmanager::beginthreadaffinity —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="42185-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42185-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42185-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="42185-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="42185-105">Return Value</span></span>  
  
|<span data-ttu-id="42185-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42185-106">HRESULT</span></span>|<span data-ttu-id="42185-107">Opis</span><span class="sxs-lookup"><span data-stu-id="42185-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42185-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="42185-108">S_OK</span></span>|`EndThreadAffinity` <span data-ttu-id="42185-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="42185-109">returned successfully.</span></span>|  
|<span data-ttu-id="42185-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42185-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42185-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="42185-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42185-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42185-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42185-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="42185-113">The call timed out.</span></span>|  
|<span data-ttu-id="42185-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42185-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42185-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="42185-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42185-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42185-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42185-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="42185-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42185-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42185-118">E_FAIL</span></span>|<span data-ttu-id="42185-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="42185-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42185-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="42185-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42185-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="42185-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42185-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="42185-122">E_UNEXPECTED</span></span>|`EndThreadAffinity` <span data-ttu-id="42185-123">Wywołano bez wcześniej odpowiedniego wywołania `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="42185-123">was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42185-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42185-124">Remarks</span></span>  
 <span data-ttu-id="42185-125">Środowisko CLR wywołuje odpowiedniego `BeginThreadAffinity` na bieżące zadanie przed wywołaniem `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="42185-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="42185-126">W przypadku braku takich odpowiedniego wywołania implementacji hosta [ihosttaskmanager —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) powinien zwrócić wartość E_UNEXPECTED, a nie podejmuj żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="42185-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42185-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42185-127">Requirements</span></span>  
 <span data-ttu-id="42185-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42185-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42185-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42185-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42185-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42185-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="42185-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="42185-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="42185-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42185-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="42185-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="42185-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="42185-134">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="42185-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="42185-135">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="42185-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="42185-136">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="42185-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
