---
title: IHostSemaphore::ReleaseSemaphore — Metoda
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82ae78d7e5b91c0955a0be8e8d85f4421dfc1871
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474316"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="6b08c-102">IHostSemaphore::ReleaseSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b08c-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="6b08c-103">Zwiększa liczbę bieżącego [ihostsemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) wystąpienia według określonej ilości.</span><span class="sxs-lookup"><span data-stu-id="6b08c-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b08c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b08c-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b08c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b08c-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="6b08c-106">[in] Wielkość, o którą należy zwiększyć liczbę bieżącego `IHostSemaphore` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6b08c-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="6b08c-107">Ta wartość musi być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="6b08c-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="6b08c-108">[out] Wskaźnik do poprzedniego liczba lub wartość null, jeśli obiekt wywołujący nie wymaga poprzedniego.</span><span class="sxs-lookup"><span data-stu-id="6b08c-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b08c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b08c-109">Return Value</span></span>  
  
|<span data-ttu-id="6b08c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b08c-110">HRESULT</span></span>|<span data-ttu-id="6b08c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6b08c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b08c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b08c-112">S_OK</span></span>|<span data-ttu-id="6b08c-113">`ReleaseSemaphore` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6b08c-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="6b08c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b08c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b08c-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b08c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b08c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b08c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b08c-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b08c-117">The call timed out.</span></span>|  
|<span data-ttu-id="6b08c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b08c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b08c-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6b08c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b08c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b08c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b08c-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6b08c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b08c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b08c-122">E_FAIL</span></span>|<span data-ttu-id="6b08c-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6b08c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b08c-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6b08c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b08c-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b08c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b08c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b08c-126">Remarks</span></span>  
 <span data-ttu-id="6b08c-127">Środowisko CLR jest zazwyczaj wywołuje `ReleaseSemaphore` celu powiadomienia hosta, że zakończył przy użyciu zasobów, przekazując wartość 1 dla `lReleaseCount` parametru.</span><span class="sxs-lookup"><span data-stu-id="6b08c-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b08c-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b08c-128">Requirements</span></span>  
 <span data-ttu-id="6b08c-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b08c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b08c-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b08c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b08c-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b08c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b08c-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b08c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b08c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b08c-133">See also</span></span>
- [<span data-ttu-id="6b08c-134">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b08c-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6b08c-135">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b08c-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="6b08c-136">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b08c-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="6b08c-137">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b08c-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="6b08c-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b08c-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
