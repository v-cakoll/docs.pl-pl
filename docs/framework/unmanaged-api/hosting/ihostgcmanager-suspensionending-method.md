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
ms.openlocfilehash: cf915af48262a0f48e85623de95b76ad94d860b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573299"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="87bae-102">IHostGCManager::SuspensionEnding — Metoda</span><span class="sxs-lookup"><span data-stu-id="87bae-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="87bae-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wznawia wykonywanie zadań w wątkach, które została wstrzymana dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="87bae-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87bae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87bae-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87bae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87bae-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="87bae-106">[in] Generacjach wyrzucania, po prostu kończy, z którego wątek jest wznawiana.</span><span class="sxs-lookup"><span data-stu-id="87bae-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87bae-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="87bae-107">Return Value</span></span>  
  
|<span data-ttu-id="87bae-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87bae-108">HRESULT</span></span>|<span data-ttu-id="87bae-109">Opis</span><span class="sxs-lookup"><span data-stu-id="87bae-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87bae-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="87bae-110">S_OK</span></span>|<span data-ttu-id="87bae-111">`SuspensionEnding` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="87bae-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="87bae-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87bae-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87bae-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="87bae-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87bae-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87bae-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87bae-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="87bae-115">The call timed out.</span></span>|  
|<span data-ttu-id="87bae-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87bae-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87bae-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="87bae-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87bae-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87bae-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87bae-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="87bae-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87bae-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87bae-120">E_FAIL</span></span>|<span data-ttu-id="87bae-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="87bae-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87bae-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="87bae-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87bae-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="87bae-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87bae-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87bae-124">Remarks</span></span>  
 <span data-ttu-id="87bae-125">CLR wywołuje `SuspensionEnding` po wykonuje wyrzucanie elementów bezużytecznych poinformować hosta, wznawia wykonanie wątku.</span><span class="sxs-lookup"><span data-stu-id="87bae-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87bae-126">Harmonogram nie wprowadzone wywołanie metody z wątku.</span><span class="sxs-lookup"><span data-stu-id="87bae-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87bae-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87bae-127">Requirements</span></span>  
 <span data-ttu-id="87bae-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87bae-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87bae-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87bae-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87bae-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87bae-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87bae-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87bae-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87bae-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87bae-132">See also</span></span>
- [<span data-ttu-id="87bae-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="87bae-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="87bae-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87bae-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="87bae-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="87bae-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="87bae-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87bae-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="87bae-137">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="87bae-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
