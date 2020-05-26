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
ms.openlocfilehash: 2436809f35d5c46416f48987cc92feb51d291a6a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804881"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="3055e-102">IHostCrst::SetSpinCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="3055e-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="3055e-103">Ustawia liczbę obrotów dla bieżącego wystąpienia [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3055e-103">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3055e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3055e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3055e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3055e-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="3055e-106">podczas Nowa liczba obrotów dla bieżącego `IHostCrst` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3055e-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3055e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3055e-107">Return Value</span></span>  
  
|<span data-ttu-id="3055e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3055e-108">HRESULT</span></span>|<span data-ttu-id="3055e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3055e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3055e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3055e-110">S_OK</span></span>|<span data-ttu-id="3055e-111">`SetSpinCount`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="3055e-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="3055e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3055e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3055e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3055e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3055e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3055e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3055e-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="3055e-115">The call timed out.</span></span>|  
|<span data-ttu-id="3055e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3055e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3055e-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3055e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3055e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3055e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3055e-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="3055e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3055e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3055e-120">E_FAIL</span></span>|<span data-ttu-id="3055e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3055e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3055e-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="3055e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3055e-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3055e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3055e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3055e-124">Remarks</span></span>  
 <span data-ttu-id="3055e-125">W przypadku systemów wieloprocesorowych, jeśli Sekcja krytyczna reprezentowana przez bieżące `IHostCrst` wystąpienie jest niedostępna, wywołujący wątek zostanie `dwSpinCount` opóźniony przed wywołaniem [IHostSemaphore:: Poczekaj](ihostsemaphore-wait-method.md) na semafor skojarzony z sekcją krytyczną.</span><span class="sxs-lookup"><span data-stu-id="3055e-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="3055e-126">Jeśli Sekcja krytyczna zostanie zwolniona podczas operacji pokrętła, wątek wywołujący unika operacji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="3055e-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="3055e-127">Użycie `dwSpinCount` jest identyczne z użyciem parametru o tej samej nazwie w `InitializeCriticalSectionAndSpinCount` funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="3055e-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3055e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3055e-128">Requirements</span></span>  
 <span data-ttu-id="3055e-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3055e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3055e-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3055e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3055e-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3055e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3055e-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3055e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3055e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3055e-133">See also</span></span>

- [<span data-ttu-id="3055e-134">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3055e-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="3055e-135">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="3055e-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="3055e-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3055e-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
