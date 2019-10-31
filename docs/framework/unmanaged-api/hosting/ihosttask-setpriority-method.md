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
ms.openlocfilehash: c64cee9ec9b62d87e0c4ae1aafaff59bb985ec95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121356"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="17d3f-102">IHostTask::SetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="17d3f-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="17d3f-103">Żądania, dla których Host dostosowuje poziom priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="17d3f-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17d3f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17d3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17d3f-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="17d3f-106">podczas Liczba całkowita reprezentująca żądaną wartość priorytetu wątku dla zadania reprezentowanego przez bieżące wystąpienie `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="17d3f-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17d3f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="17d3f-107">Return Value</span></span>  
  
|<span data-ttu-id="17d3f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17d3f-108">HRESULT</span></span>|<span data-ttu-id="17d3f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="17d3f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17d3f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="17d3f-110">S_OK</span></span>|<span data-ttu-id="17d3f-111">`SetPriority` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="17d3f-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="17d3f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17d3f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17d3f-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="17d3f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17d3f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17d3f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17d3f-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="17d3f-115">The call timed out.</span></span>|  
|<span data-ttu-id="17d3f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17d3f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17d3f-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="17d3f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17d3f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17d3f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17d3f-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="17d3f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17d3f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17d3f-120">E_FAIL</span></span>|<span data-ttu-id="17d3f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="17d3f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17d3f-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="17d3f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17d3f-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17d3f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17d3f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17d3f-124">Remarks</span></span>  
 <span data-ttu-id="17d3f-125">Wątki otrzymują czas przetwarzania przy użyciu systemu działania okrężnego, który jest częściowo oparty na poziomie priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="17d3f-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="17d3f-126">`SetPriority` umożliwia środowisku CLR Ustawianie tego poziomu priorytetu wątku dla bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="17d3f-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="17d3f-127">Obsługiwane są następujące wartości `newPriority`.</span><span class="sxs-lookup"><span data-stu-id="17d3f-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="17d3f-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="17d3f-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="17d3f-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="17d3f-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="17d3f-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="17d3f-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="17d3f-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="17d3f-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="17d3f-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="17d3f-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="17d3f-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="17d3f-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="17d3f-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="17d3f-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="17d3f-135">Wywołania CLR `SetPriority`, gdy wartość <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> jest modyfikowana przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17d3f-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="17d3f-136">Host może definiować własne algorytmy do przypisywania priorytetów wątków i jest bezpłatny do ignorowania tego żądania.</span><span class="sxs-lookup"><span data-stu-id="17d3f-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17d3f-137">`SetPriority` nie zgłasza tego, czy poziom priorytetu wątku został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="17d3f-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="17d3f-138">Wywołaj [IHostTask:: GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) , aby określić wartość poziomu priorytetu wątku zadania.</span><span class="sxs-lookup"><span data-stu-id="17d3f-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="17d3f-139">Wartości poziomu priorytetu wątku są definiowane przez funkcję `SetThreadPriority` Win32.</span><span class="sxs-lookup"><span data-stu-id="17d3f-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="17d3f-140">Więcej informacji o priorytecie wątku znajduje się w dokumentacji platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="17d3f-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d3f-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17d3f-141">Requirements</span></span>  
 <span data-ttu-id="17d3f-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17d3f-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d3f-143">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17d3f-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17d3f-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17d3f-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17d3f-145">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d3f-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d3f-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17d3f-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="17d3f-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="17d3f-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="17d3f-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="17d3f-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="17d3f-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="17d3f-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="17d3f-150">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="17d3f-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="17d3f-151">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="17d3f-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
