---
title: "IHostTaskManager::BeginDelayAbort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a6b37c87f26013dab95f7607e03463437b9797a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="b11d9-102">IHostTaskManager::BeginDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="b11d9-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="b11d9-103">Powiadamia hosta, którego kod zarządzany jest wprowadzanie okres, w którym nie musi być zostało przerwane bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="b11d9-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b11d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b11d9-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b11d9-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b11d9-105">Return Value</span></span>  
  
|<span data-ttu-id="b11d9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b11d9-106">HRESULT</span></span>|<span data-ttu-id="b11d9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b11d9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b11d9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b11d9-108">S_OK</span></span>|<span data-ttu-id="b11d9-109">`BeginDelayAbort`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b11d9-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="b11d9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b11d9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b11d9-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b11d9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b11d9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b11d9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b11d9-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b11d9-113">The call timed out.</span></span>|  
|<span data-ttu-id="b11d9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b11d9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b11d9-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b11d9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b11d9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b11d9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b11d9-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b11d9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b11d9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b11d9-118">E_FAIL</span></span>|<span data-ttu-id="b11d9-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b11d9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b11d9-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b11d9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b11d9-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b11d9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b11d9-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="b11d9-122">E_UNEXPECTED</span></span>|<span data-ttu-id="b11d9-123">`BeginDelayAbort`została już wywołana, ale odpowiedniego wywołania [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) jeszcze nie został odebrany.</span><span class="sxs-lookup"><span data-stu-id="b11d9-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b11d9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b11d9-124">Remarks</span></span>  
 <span data-ttu-id="b11d9-125">Host nie musi przerwać bieżącego zadania do `EndDelayAbort` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b11d9-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="b11d9-126">Jeśli wywołanie innego `BeginDelayAbort` staje się bez interwencji wywołania do `EndDelayAbort`, hosta powinien zwrócić E_UNEXPECTED z `BeginDelayAbort`, a powinien Nie podejmuj żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="b11d9-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b11d9-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b11d9-127">Requirements</span></span>  
 <span data-ttu-id="b11d9-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b11d9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b11d9-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b11d9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b11d9-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b11d9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b11d9-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b11d9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b11d9-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b11d9-132">See Also</span></span>  
 [<span data-ttu-id="b11d9-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b11d9-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="b11d9-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b11d9-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b11d9-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b11d9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="b11d9-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b11d9-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
