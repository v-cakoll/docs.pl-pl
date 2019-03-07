---
title: IHostSemaphore::Wait — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9933948a5e67b91106cdadc6f747c1b1c4121813
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489998"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="a2fea-102">IHostSemaphore::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2fea-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="a2fea-103">Powoduje, że bieżący [ihostsemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) wystąpienie do odczekania aż do jego właścicielem jest lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="a2fea-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2fea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2fea-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2fea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2fea-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="a2fea-106">[in] Liczba milisekund oczekiwania przed zwróceniem, jeśli bieżący `IHostSemaphore` wystąpienia nie jest własnością.</span><span class="sxs-lookup"><span data-stu-id="a2fea-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="a2fea-107">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości, określając akcję host powinien wykonać, jeśli operacja bloków.</span><span class="sxs-lookup"><span data-stu-id="a2fea-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2fea-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2fea-108">Return Value</span></span>  
  
|<span data-ttu-id="a2fea-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2fea-109">HRESULT</span></span>|<span data-ttu-id="a2fea-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a2fea-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2fea-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2fea-111">S_OK</span></span>|<span data-ttu-id="a2fea-112">`Wait` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a2fea-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="a2fea-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2fea-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2fea-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a2fea-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2fea-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2fea-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2fea-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a2fea-116">The call timed out.</span></span>|  
|<span data-ttu-id="a2fea-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2fea-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2fea-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a2fea-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2fea-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2fea-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2fea-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a2fea-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2fea-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2fea-121">E_FAIL</span></span>|<span data-ttu-id="a2fea-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a2fea-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2fea-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a2fea-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2fea-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a2fea-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2fea-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="a2fea-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="a2fea-126">Host wykrył zakleszczenie w przedziale czasu oczekiwania, a wybrano bieżącego `IHostSemaphore` wystąpienia jako ofiara zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a2fea-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2fea-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2fea-127">Requirements</span></span>  
 <span data-ttu-id="a2fea-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2fea-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2fea-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2fea-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2fea-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2fea-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2fea-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2fea-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2fea-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2fea-132">See also</span></span>
- [<span data-ttu-id="a2fea-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2fea-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a2fea-134">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2fea-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="a2fea-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2fea-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="a2fea-136">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2fea-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="a2fea-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2fea-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
