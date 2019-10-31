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
ms.openlocfilehash: a8642235cda359b849c49a35ab565397402c37d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130514"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="f64c2-102">IHostCrst::SetSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="f64c2-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="f64c2-103">Ustawia liczbę obrotów dla bieżącego wystąpienia [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f64c2-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f64c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f64c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f64c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f64c2-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="f64c2-106">podczas Nowa liczba obrotów dla bieżącego wystąpienia `IHostCrst`.</span><span class="sxs-lookup"><span data-stu-id="f64c2-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f64c2-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f64c2-107">Return Value</span></span>  
  
|<span data-ttu-id="f64c2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f64c2-108">HRESULT</span></span>|<span data-ttu-id="f64c2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f64c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f64c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f64c2-110">S_OK</span></span>|<span data-ttu-id="f64c2-111">`SetSpinCount` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f64c2-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="f64c2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f64c2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f64c2-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f64c2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f64c2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f64c2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f64c2-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f64c2-115">The call timed out.</span></span>|  
|<span data-ttu-id="f64c2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f64c2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f64c2-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f64c2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f64c2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f64c2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f64c2-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f64c2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f64c2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f64c2-120">E_FAIL</span></span>|<span data-ttu-id="f64c2-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f64c2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f64c2-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f64c2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f64c2-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f64c2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f64c2-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f64c2-124">Remarks</span></span>  
 <span data-ttu-id="f64c2-125">W systemach wieloprocesorowych, jeśli Sekcja krytyczna reprezentowana przez bieżące wystąpienie `IHostCrst` jest niedostępna, wątek wywołujący obraca się `dwSpinCount` razy przed wywołaniem [IHostSemaphore:: Poczekaj](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) na semafory skojarzone z sekcją krytyczną.</span><span class="sxs-lookup"><span data-stu-id="f64c2-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="f64c2-126">Jeśli Sekcja krytyczna zostanie zwolniona podczas operacji pokrętła, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="f64c2-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="f64c2-127">Użycie `dwSpinCount` jest identyczne z użyciem parametru o tej samej nazwie w funkcji Win32 `InitializeCriticalSectionAndSpinCount`.</span><span class="sxs-lookup"><span data-stu-id="f64c2-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f64c2-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f64c2-128">Requirements</span></span>  
 <span data-ttu-id="f64c2-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f64c2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f64c2-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f64c2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f64c2-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f64c2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f64c2-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f64c2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64c2-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f64c2-133">See also</span></span>

- [<span data-ttu-id="f64c2-134">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f64c2-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f64c2-135">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="f64c2-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="f64c2-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f64c2-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
