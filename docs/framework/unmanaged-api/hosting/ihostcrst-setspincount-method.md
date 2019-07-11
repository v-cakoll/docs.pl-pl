---
title: IHostCrst::SetSpinCount — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdbce5e61f2013513d2079b5a958270319d34857
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763762"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="0e773-102">IHostCrst::SetSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="0e773-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="0e773-103">Ustawia liczbę pokrętła dla bieżącego [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0e773-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e773-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e773-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e773-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e773-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="0e773-106">[in] Liczba nowych pokrętła, dla bieżącego `IHostCrst` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0e773-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e773-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0e773-107">Return Value</span></span>  
  
|<span data-ttu-id="0e773-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e773-108">HRESULT</span></span>|<span data-ttu-id="0e773-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0e773-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e773-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e773-110">S_OK</span></span>|<span data-ttu-id="0e773-111">`SetSpinCount` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0e773-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="0e773-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e773-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e773-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0e773-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e773-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e773-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e773-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0e773-115">The call timed out.</span></span>|  
|<span data-ttu-id="0e773-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e773-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e773-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="0e773-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e773-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e773-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e773-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0e773-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e773-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e773-120">E_FAIL</span></span>|<span data-ttu-id="0e773-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0e773-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e773-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0e773-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e773-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0e773-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e773-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e773-124">Remarks</span></span>  
 <span data-ttu-id="0e773-125">W systemach wieloprocesorowych, jeśli sekcję krytyczną, reprezentowane przez bieżącą `IHostCrst` wystąpienia jest niedostępna, wątek uruchamia `dwSpinCount` czasy przed wywołaniem [ihostsemaphore::wait —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) na semafor skojarzone sekcja krytycznego.</span><span class="sxs-lookup"><span data-stu-id="0e773-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="0e773-126">Jeśli podczas operacji pokrętła zwolniony sekcję krytyczną, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="0e773-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="0e773-127">Użycie `dwSpinCount` jest taka sama jak użycie parametru o takiej samej nazwie w Win32 `InitializeCriticalSectionAndSpinCount` funkcji.</span><span class="sxs-lookup"><span data-stu-id="0e773-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e773-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e773-128">Requirements</span></span>  
 <span data-ttu-id="0e773-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e773-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e773-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e773-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e773-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e773-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e773-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e773-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e773-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e773-133">See also</span></span>

- [<span data-ttu-id="0e773-134">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e773-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0e773-135">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e773-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="0e773-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e773-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
