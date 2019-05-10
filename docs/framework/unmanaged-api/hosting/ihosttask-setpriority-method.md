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
ms.openlocfilehash: b05960eac85140a1539877eccf2d0ccdf053e76b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64657927"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="aed9c-102">IHostTask::SetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="aed9c-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="aed9c-103">Na poziomie żądania, czy host zmienić priorytet wątku dla zadania, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aed9c-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aed9c-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aed9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aed9c-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="aed9c-106">[in] Liczba całkowita, która reprezentuje wartość priorytetu wątku żądanego zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aed9c-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aed9c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aed9c-107">Return Value</span></span>  
  
|<span data-ttu-id="aed9c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aed9c-108">HRESULT</span></span>|<span data-ttu-id="aed9c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aed9c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aed9c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aed9c-110">S_OK</span></span>|<span data-ttu-id="aed9c-111">`SetPriority` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="aed9c-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="aed9c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aed9c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aed9c-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aed9c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aed9c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aed9c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aed9c-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aed9c-115">The call timed out.</span></span>|  
|<span data-ttu-id="aed9c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aed9c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aed9c-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="aed9c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aed9c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aed9c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aed9c-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aed9c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aed9c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aed9c-120">E_FAIL</span></span>|<span data-ttu-id="aed9c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aed9c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aed9c-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aed9c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aed9c-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aed9c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aed9c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aed9c-124">Remarks</span></span>  
 <span data-ttu-id="aed9c-125">Wątki są przyznane przetwarzania czasu przy użyciu działania okrężnego systemu, w którym jest częściowo oparte na poziom priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="aed9c-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="aed9c-126">`SetPriority` Umożliwia środowisku CLR ustawić ten poziom priorytetu wątku dla bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="aed9c-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="aed9c-127">Następujące `newPriority` wartości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="aed9c-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="aed9c-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="aed9c-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="aed9c-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="aed9c-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="aed9c-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="aed9c-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="aed9c-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="aed9c-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="aed9c-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="aed9c-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="aed9c-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="aed9c-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="aed9c-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="aed9c-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="aed9c-135">CLR wywołuje `SetPriority` po wartości <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> jest modyfikowany przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aed9c-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="aed9c-136">Hosta można zdefiniować własne algorytmów do przypisywania priorytetu wątku i jest bezpłatna do zignorowania tego żądania.</span><span class="sxs-lookup"><span data-stu-id="aed9c-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed9c-137">`SetPriority` nie raportuje, czy został zmieniony poziom priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="aed9c-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="aed9c-138">Wywołaj [ihosttask::getpriority —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) do określenia wartości poziom priorytetu wątku dla zadania podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="aed9c-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="aed9c-139">Wartości poziomu priorytetu wątku są definiowane przez Win32 `SetThreadPriority` funkcji.</span><span class="sxs-lookup"><span data-stu-id="aed9c-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="aed9c-140">Więcej informacji na temat priorytetu wątku znajduje się w dokumentacji platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="aed9c-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aed9c-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aed9c-141">Requirements</span></span>  
 <span data-ttu-id="aed9c-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aed9c-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aed9c-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aed9c-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aed9c-144">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aed9c-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aed9c-145">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aed9c-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed9c-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aed9c-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="aed9c-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed9c-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="aed9c-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed9c-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="aed9c-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed9c-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="aed9c-150">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="aed9c-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="aed9c-151">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aed9c-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
