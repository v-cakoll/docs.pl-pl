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
ms.openlocfilehash: 0e977133d722edc7d090d07cd117ee282a8d29cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753583"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="db444-102">IHostSemaphore::ReleaseSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="db444-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="db444-103">Zwiększa liczbę bieżącego [ihostsemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) wystąpienia według określonej ilości.</span><span class="sxs-lookup"><span data-stu-id="db444-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db444-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db444-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db444-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db444-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="db444-106">[in] Wielkość, o którą należy zwiększyć liczbę bieżącego `IHostSemaphore` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="db444-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="db444-107">Ta wartość musi być większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="db444-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="db444-108">[out] Wskaźnik do poprzedniego liczba lub wartość null, jeśli obiekt wywołujący nie wymaga poprzedniego.</span><span class="sxs-lookup"><span data-stu-id="db444-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db444-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="db444-109">Return Value</span></span>  
  
|<span data-ttu-id="db444-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db444-110">HRESULT</span></span>|<span data-ttu-id="db444-111">Opis</span><span class="sxs-lookup"><span data-stu-id="db444-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db444-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="db444-112">S_OK</span></span>|<span data-ttu-id="db444-113">`ReleaseSemaphore` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="db444-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="db444-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db444-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db444-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="db444-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db444-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db444-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db444-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="db444-117">The call timed out.</span></span>|  
|<span data-ttu-id="db444-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db444-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db444-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="db444-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db444-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db444-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db444-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="db444-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db444-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db444-122">E_FAIL</span></span>|<span data-ttu-id="db444-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="db444-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db444-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="db444-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db444-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db444-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db444-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db444-126">Remarks</span></span>  
 <span data-ttu-id="db444-127">Środowisko CLR jest zazwyczaj wywołuje `ReleaseSemaphore` celu powiadomienia hosta, że zakończył przy użyciu zasobów, przekazując wartość 1 dla `lReleaseCount` parametru.</span><span class="sxs-lookup"><span data-stu-id="db444-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db444-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db444-128">Requirements</span></span>  
 <span data-ttu-id="db444-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db444-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db444-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db444-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db444-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db444-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db444-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db444-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db444-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db444-133">See also</span></span>

- [<span data-ttu-id="db444-134">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="db444-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="db444-135">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="db444-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="db444-136">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="db444-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="db444-137">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="db444-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="db444-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="db444-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
