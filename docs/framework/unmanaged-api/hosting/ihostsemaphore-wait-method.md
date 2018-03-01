---
title: "IHostSemaphore::Wait — Metoda"
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
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15c86ee8b1de22f07b01290f5a830afd95427ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="c6a5e-102">IHostSemaphore::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6a5e-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="c6a5e-103">Powoduje, że bieżący [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) wystąpienia poczekać, aż należy lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6a5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6a5e-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6a5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6a5e-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="c6a5e-106">[in] Wyrażony w milisekundach czas oczekiwania przed zwróceniem, jeśli bieżący `IHostSemaphore` wystąpienia nie jest właścicielem.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="c6a5e-107">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości, określając akcję hosta powinien wykonać, jeśli ten bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6a5e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6a5e-108">Return Value</span></span>  
  
|<span data-ttu-id="c6a5e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6a5e-109">HRESULT</span></span>|<span data-ttu-id="c6a5e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c6a5e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6a5e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6a5e-111">S_OK</span></span>|<span data-ttu-id="c6a5e-112">`Wait`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="c6a5e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6a5e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6a5e-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6a5e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6a5e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6a5e-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-116">The call timed out.</span></span>|  
|<span data-ttu-id="c6a5e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6a5e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6a5e-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6a5e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6a5e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6a5e-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6a5e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6a5e-121">E_FAIL</span></span>|<span data-ttu-id="c6a5e-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6a5e-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6a5e-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c6a5e-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="c6a5e-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="c6a5e-126">Host wykrył zakleszczenie w interwale oczekiwania, a wybrano bieżącego `IHostSemaphore` wystąpienia jako ofiara zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="c6a5e-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6a5e-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6a5e-127">Requirements</span></span>  
 <span data-ttu-id="c6a5e-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6a5e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6a5e-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6a5e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6a5e-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6a5e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6a5e-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6a5e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a5e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6a5e-132">See Also</span></span>  
 [<span data-ttu-id="c6a5e-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a5e-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c6a5e-134">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a5e-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="c6a5e-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a5e-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="c6a5e-136">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a5e-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="c6a5e-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6a5e-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
