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
ms.openlocfilehash: 533e3d715b46b4ef6d473795a010fa3ad297ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913751"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="11946-102">IHostTask::SetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="11946-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="11946-103">Żądania, dla których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="11946-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11946-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11946-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11946-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11946-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="11946-106">podczas Liczba całkowita reprezentująca żądaną wartość priorytetu wątku dla zadania reprezentowanego przez bieżące `IHostTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="11946-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11946-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11946-107">Return Value</span></span>  
  
|<span data-ttu-id="11946-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11946-108">HRESULT</span></span>|<span data-ttu-id="11946-109">Opis</span><span class="sxs-lookup"><span data-stu-id="11946-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11946-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="11946-110">S_OK</span></span>|<span data-ttu-id="11946-111">`SetPriority`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="11946-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="11946-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11946-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11946-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="11946-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11946-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11946-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11946-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="11946-115">The call timed out.</span></span>|  
|<span data-ttu-id="11946-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11946-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11946-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="11946-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11946-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11946-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11946-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="11946-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11946-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11946-120">E_FAIL</span></span>|<span data-ttu-id="11946-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11946-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11946-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="11946-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11946-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11946-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11946-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11946-124">Remarks</span></span>  
 <span data-ttu-id="11946-125">Wątki otrzymują czas przetwarzania przy użyciu systemu działania okrężnego, który jest częściowo oparty na poziomie priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="11946-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="11946-126">`SetPriority`umożliwia środowisku CLR Ustawianie tego poziomu priorytetu wątku dla bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="11946-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="11946-127">Obsługiwane są `newPriority` następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="11946-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="11946-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="11946-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="11946-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="11946-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="11946-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="11946-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="11946-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="11946-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="11946-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="11946-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="11946-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="11946-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="11946-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="11946-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="11946-135">Środowisko CLR wywołuje `SetPriority` , gdy wartość <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> elementu jest modyfikowana przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11946-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="11946-136">Host może definiować własne algorytmy do przypisywania priorytetów wątków i jest bezpłatny do ignorowania tego żądania.</span><span class="sxs-lookup"><span data-stu-id="11946-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11946-137">`SetPriority`nie zgłasza tego, czy poziom priorytetu wątku został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="11946-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="11946-138">Wywołaj [IHostTask:: GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) , aby określić wartość poziomu priorytetu wątku zadania.</span><span class="sxs-lookup"><span data-stu-id="11946-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="11946-139">Wartości poziomu priorytetu wątku są definiowane przez funkcję `SetThreadPriority` Win32.</span><span class="sxs-lookup"><span data-stu-id="11946-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="11946-140">Więcej informacji o priorytecie wątku znajduje się w dokumentacji platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="11946-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11946-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11946-141">Requirements</span></span>  
 <span data-ttu-id="11946-142">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11946-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11946-143">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="11946-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11946-144">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11946-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11946-145">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11946-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11946-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11946-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="11946-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="11946-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="11946-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11946-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="11946-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="11946-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="11946-150">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="11946-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="11946-151">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11946-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
