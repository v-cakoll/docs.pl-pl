---
title: IHostTask::SetPriority — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9ecdeb4df6210805490586f1818298025fc036
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749941"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="23a9e-102">IHostTask::SetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="23a9e-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="23a9e-103">Na poziomie żądania, czy host zmienić priorytet wątku dla zadania, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="23a9e-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23a9e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23a9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23a9e-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="23a9e-106">[in] Liczba całkowita, która reprezentuje wartość priorytetu wątku żądanego zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="23a9e-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23a9e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="23a9e-107">Return Value</span></span>  
  
|<span data-ttu-id="23a9e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23a9e-108">HRESULT</span></span>|<span data-ttu-id="23a9e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="23a9e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23a9e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="23a9e-110">S_OK</span></span>|<span data-ttu-id="23a9e-111">`SetPriority` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="23a9e-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="23a9e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23a9e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23a9e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="23a9e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23a9e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23a9e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23a9e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="23a9e-115">The call timed out.</span></span>|  
|<span data-ttu-id="23a9e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23a9e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23a9e-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="23a9e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23a9e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23a9e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23a9e-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="23a9e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23a9e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23a9e-120">E_FAIL</span></span>|<span data-ttu-id="23a9e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="23a9e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23a9e-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="23a9e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23a9e-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="23a9e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23a9e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23a9e-124">Remarks</span></span>  
 <span data-ttu-id="23a9e-125">Wątki są przyznane przetwarzania czasu przy użyciu działania okrężnego systemu, w którym jest częściowo oparte na poziom priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="23a9e-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="23a9e-126">`SetPriority` Umożliwia środowisku CLR ustawić ten poziom priorytetu wątku dla bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="23a9e-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="23a9e-127">Następujące `newPriority` wartości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="23a9e-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="23a9e-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="23a9e-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="23a9e-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="23a9e-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="23a9e-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="23a9e-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="23a9e-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="23a9e-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="23a9e-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="23a9e-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="23a9e-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="23a9e-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="23a9e-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="23a9e-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="23a9e-135">CLR wywołuje `SetPriority` po wartości <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> jest modyfikowany przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="23a9e-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="23a9e-136">Hosta można zdefiniować własne algorytmów do przypisywania priorytetu wątku i jest bezpłatna do zignorowania tego żądania.</span><span class="sxs-lookup"><span data-stu-id="23a9e-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23a9e-137">`SetPriority` nie raportuje, czy został zmieniony poziom priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="23a9e-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="23a9e-138">Wywołaj [ihosttask::getpriority —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) do określenia wartości poziom priorytetu wątku dla zadania podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="23a9e-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="23a9e-139">Wartości poziomu priorytetu wątku są definiowane przez Win32 `SetThreadPriority` funkcji.</span><span class="sxs-lookup"><span data-stu-id="23a9e-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="23a9e-140">Więcej informacji na temat priorytetu wątku znajduje się w dokumentacji platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="23a9e-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a9e-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23a9e-141">Requirements</span></span>  
 <span data-ttu-id="23a9e-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a9e-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a9e-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="23a9e-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23a9e-144">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23a9e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23a9e-145">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a9e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a9e-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23a9e-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="23a9e-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="23a9e-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="23a9e-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="23a9e-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="23a9e-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="23a9e-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="23a9e-150">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="23a9e-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="23a9e-151">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="23a9e-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
