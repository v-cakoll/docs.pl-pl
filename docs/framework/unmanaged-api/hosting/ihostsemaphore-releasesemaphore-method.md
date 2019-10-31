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
ms.openlocfilehash: 33a92365e7765befe669439eabefac607232ff15
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139461"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="e3c1a-102">IHostSemaphore::ReleaseSemaphore — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3c1a-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="e3c1a-103">Zwiększa liczbę wystąpień bieżącego wystąpienia [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) o określoną liczbę.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3c1a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c1a-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="e3c1a-106">podczas Wartość, według której ma zostać zwiększona liczba bieżących wystąpień `IHostSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="e3c1a-107">Ta wartość musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="e3c1a-108">określoną Wskaźnik do poprzedniej liczby lub wartość null, jeśli obiekt wywołujący nie wymaga poprzedniej liczby.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3c1a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3c1a-109">Return Value</span></span>  
  
|<span data-ttu-id="e3c1a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3c1a-110">HRESULT</span></span>|<span data-ttu-id="e3c1a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e3c1a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3c1a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3c1a-112">S_OK</span></span>|<span data-ttu-id="e3c1a-113">`ReleaseSemaphore` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="e3c1a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e3c1a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e3c1a-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e3c1a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e3c1a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e3c1a-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-117">The call timed out.</span></span>|  
|<span data-ttu-id="e3c1a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e3c1a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e3c1a-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e3c1a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e3c1a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e3c1a-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e3c1a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e3c1a-122">E_FAIL</span></span>|<span data-ttu-id="e3c1a-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e3c1a-124">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e3c1a-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3c1a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3c1a-126">Remarks</span></span>  
 <span data-ttu-id="e3c1a-127">Środowisko CLR zwykle wywołuje `ReleaseSemaphore`, aby powiadomić hosta, że zakończył korzystanie z zasobu, przekazując wartość 1 dla parametru `lReleaseCount`.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c1a-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3c1a-128">Requirements</span></span>  
 <span data-ttu-id="e3c1a-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c1a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c1a-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3c1a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3c1a-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3c1a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3c1a-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c1a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c1a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3c1a-133">See also</span></span>

- [<span data-ttu-id="e3c1a-134">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c1a-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e3c1a-135">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c1a-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e3c1a-136">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c1a-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e3c1a-137">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c1a-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="e3c1a-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c1a-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
