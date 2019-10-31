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
ms.openlocfilehash: bf09f7bc6c3e3aabfc16f9cad277c46be024b01d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139452"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="fef15-102">IHostSemaphore::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="fef15-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="fef15-103">Powoduje, że bieżące wystąpienie [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) zaczeka, aż jego właścicielem lub określony czas upłynął.</span><span class="sxs-lookup"><span data-stu-id="fef15-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fef15-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fef15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fef15-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="fef15-106">podczas Liczba milisekund oczekiwania przed zwróceniem, jeśli bieżące wystąpienie `IHostSemaphore` nie należy do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fef15-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="fef15-107">podczas Jedna z wartości [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , która określa, jaką akcję powinien wykonać host, jeśli ta operacja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="fef15-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fef15-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fef15-108">Return Value</span></span>  
  
|<span data-ttu-id="fef15-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fef15-109">HRESULT</span></span>|<span data-ttu-id="fef15-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fef15-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fef15-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fef15-111">S_OK</span></span>|<span data-ttu-id="fef15-112">`Wait` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fef15-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="fef15-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fef15-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fef15-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fef15-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fef15-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fef15-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fef15-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="fef15-116">The call timed out.</span></span>|  
|<span data-ttu-id="fef15-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fef15-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fef15-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fef15-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fef15-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fef15-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fef15-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="fef15-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fef15-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fef15-121">E_FAIL</span></span>|<span data-ttu-id="fef15-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fef15-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fef15-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="fef15-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fef15-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fef15-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fef15-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="fef15-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="fef15-126">Host wykrył zakleszczenie w interwale oczekiwania i wybiera bieżące wystąpienie `IHostSemaphore` jako ofiarę zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="fef15-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fef15-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fef15-127">Requirements</span></span>  
 <span data-ttu-id="fef15-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fef15-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef15-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fef15-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fef15-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fef15-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fef15-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef15-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef15-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fef15-132">See also</span></span>

- [<span data-ttu-id="fef15-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fef15-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="fef15-134">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="fef15-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="fef15-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="fef15-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="fef15-136">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="fef15-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="fef15-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fef15-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
