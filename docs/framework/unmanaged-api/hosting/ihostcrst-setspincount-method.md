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
ms.openlocfilehash: 3ca17a6814b56c0fe781cfb28a35a576f02f1943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090579"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="dbd21-102">IHostCrst::SetSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="dbd21-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="dbd21-103">Ustawia liczbę pokrętła dla bieżącego [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dbd21-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbd21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbd21-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbd21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbd21-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="dbd21-106">[in] Liczba nowych pokrętła, dla bieżącego `IHostCrst` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dbd21-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbd21-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dbd21-107">Return Value</span></span>  
  
|<span data-ttu-id="dbd21-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbd21-108">HRESULT</span></span>|<span data-ttu-id="dbd21-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dbd21-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbd21-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbd21-110">S_OK</span></span>|`SetSpinCount` <span data-ttu-id="dbd21-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="dbd21-111">returned successfully.</span></span>|  
|<span data-ttu-id="dbd21-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbd21-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbd21-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dbd21-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbd21-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbd21-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbd21-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dbd21-115">The call timed out.</span></span>|  
|<span data-ttu-id="dbd21-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbd21-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbd21-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="dbd21-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbd21-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbd21-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbd21-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dbd21-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbd21-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbd21-120">E_FAIL</span></span>|<span data-ttu-id="dbd21-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dbd21-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbd21-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dbd21-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbd21-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbd21-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbd21-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbd21-124">Remarks</span></span>  
 <span data-ttu-id="dbd21-125">W systemach wieloprocesorowych, jeśli sekcję krytyczną, reprezentowane przez bieżącą `IHostCrst` wystąpienia jest niedostępna, wątek uruchamia `dwSpinCount` czasy przed wywołaniem [ihostsemaphore::wait —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) na semafor skojarzone sekcja krytycznego.</span><span class="sxs-lookup"><span data-stu-id="dbd21-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="dbd21-126">Jeśli podczas operacji pokrętła zwolniony sekcję krytyczną, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="dbd21-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="dbd21-127">Użycie `dwSpinCount` jest taka sama jak użycie parametru o takiej samej nazwie w Win32 `InitializeCriticalSectionAndSpinCount` funkcji.</span><span class="sxs-lookup"><span data-stu-id="dbd21-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbd21-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbd21-128">Requirements</span></span>  
 <span data-ttu-id="dbd21-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbd21-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbd21-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbd21-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbd21-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbd21-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dbd21-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dbd21-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dbd21-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbd21-133">See also</span></span>

- [<span data-ttu-id="dbd21-134">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dbd21-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="dbd21-135">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dbd21-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="dbd21-136">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dbd21-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
