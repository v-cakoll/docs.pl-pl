---
title: IHostTaskManager::BeginDelayAbort — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 328462343669b3ea6bed2d86514ea348f6ae2b1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789541"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="2fc7b-102">IHostTaskManager::BeginDelayAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fc7b-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="2fc7b-103">Powiadamia hosta, którego kod zarządzany wchodzi okres, w którym musi nie przerwane bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fc7b-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2fc7b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2fc7b-105">Return Value</span></span>  
  
|<span data-ttu-id="2fc7b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fc7b-106">HRESULT</span></span>|<span data-ttu-id="2fc7b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2fc7b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fc7b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fc7b-108">S_OK</span></span>|<span data-ttu-id="2fc7b-109">`BeginDelayAbort` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="2fc7b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2fc7b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2fc7b-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2fc7b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2fc7b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2fc7b-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-113">The call timed out.</span></span>|  
|<span data-ttu-id="2fc7b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2fc7b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2fc7b-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2fc7b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2fc7b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2fc7b-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2fc7b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2fc7b-118">E_FAIL</span></span>|<span data-ttu-id="2fc7b-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2fc7b-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2fc7b-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2fc7b-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="2fc7b-122">E_UNEXPECTED</span></span>|<span data-ttu-id="2fc7b-123">`BeginDelayAbort` została już wywołana, ale odpowiedniego wywołania [enddelayabort —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) nie zostało jeszcze odebrane.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fc7b-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fc7b-124">Remarks</span></span>  
 <span data-ttu-id="2fc7b-125">Host nie musi przerwać bieżącego zadania, dopóki `EndDelayAbort` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="2fc7b-126">Jeśli wywołanie innego `BeginDelayAbort` jest wykonywana bez interwencyjnego wywołania `EndDelayAbort`, host powinien zwrócić wartość E_UNEXPECTED z `BeginDelayAbort`i powinien podejmować żadnej akcji.</span><span class="sxs-lookup"><span data-stu-id="2fc7b-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fc7b-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fc7b-127">Requirements</span></span>  
 <span data-ttu-id="2fc7b-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fc7b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fc7b-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2fc7b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2fc7b-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2fc7b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fc7b-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fc7b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc7b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fc7b-132">See also</span></span>

- [<span data-ttu-id="2fc7b-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2fc7b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2fc7b-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2fc7b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2fc7b-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2fc7b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
