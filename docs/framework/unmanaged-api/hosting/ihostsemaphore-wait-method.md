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
ms.openlocfilehash: 22d570711c293dd8c0cc6fefd198dd46d6489bea
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803536"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="1882a-102">IHostSemaphore::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="1882a-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="1882a-103">Powoduje, że bieżące wystąpienie [IHostSemaphore](ihostsemaphore-interface.md) zaczeka, aż jego właścicielem lub określony czas upłynął.</span><span class="sxs-lookup"><span data-stu-id="1882a-103">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1882a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1882a-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1882a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1882a-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="1882a-106">podczas Liczba milisekund oczekiwania przed zwróceniem, jeśli bieżące `IHostSemaphore` wystąpienie nie jest własnością.</span><span class="sxs-lookup"><span data-stu-id="1882a-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="1882a-107">podczas Jedna z wartości [WAIT_OPTION](wait-option-enumeration.md) , określając jaką akcję powinien wykonać host, jeśli ta operacja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="1882a-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1882a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1882a-108">Return Value</span></span>  
  
|<span data-ttu-id="1882a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1882a-109">HRESULT</span></span>|<span data-ttu-id="1882a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1882a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1882a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1882a-111">S_OK</span></span>|<span data-ttu-id="1882a-112">`Wait`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="1882a-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="1882a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1882a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1882a-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1882a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1882a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1882a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1882a-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="1882a-116">The call timed out.</span></span>|  
|<span data-ttu-id="1882a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1882a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1882a-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1882a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1882a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1882a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1882a-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="1882a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1882a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1882a-121">E_FAIL</span></span>|<span data-ttu-id="1882a-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1882a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1882a-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1882a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1882a-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1882a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1882a-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="1882a-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="1882a-126">Host wykrył zakleszczenie w interwale oczekiwania i wybiera bieżące `IHostSemaphore` wystąpienie jako ofiarę zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="1882a-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1882a-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1882a-127">Requirements</span></span>  
 <span data-ttu-id="1882a-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1882a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1882a-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1882a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1882a-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1882a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1882a-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1882a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1882a-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1882a-132">See also</span></span>

- [<span data-ttu-id="1882a-133">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1882a-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="1882a-134">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1882a-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="1882a-135">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="1882a-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="1882a-136">IHostSemaphore, interfejs</span><span class="sxs-lookup"><span data-stu-id="1882a-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="1882a-137">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1882a-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
