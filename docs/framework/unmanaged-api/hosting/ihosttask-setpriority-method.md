---
title: "IHostTask::SetPriority — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f9a57442b1671ef0286536215d10768636e3aa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="1ac86-102">IHostTask::SetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ac86-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="1ac86-103">Żądania, że host dostosować priorytetu wątku poziomu reprezentowanego przez bieżącego zadania [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ac86-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ac86-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ac86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ac86-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="1ac86-106">[in] Liczba całkowita, która reprezentuje wartość priorytetu wątku żądanego zadania reprezentowany przez bieżący `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ac86-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ac86-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1ac86-107">Return Value</span></span>  
  
|<span data-ttu-id="1ac86-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ac86-108">HRESULT</span></span>|<span data-ttu-id="1ac86-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1ac86-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ac86-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ac86-110">S_OK</span></span>|<span data-ttu-id="1ac86-111">`SetPriority`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1ac86-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="1ac86-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ac86-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ac86-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1ac86-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ac86-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ac86-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ac86-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1ac86-115">The call timed out.</span></span>|  
|<span data-ttu-id="1ac86-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ac86-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ac86-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1ac86-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ac86-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ac86-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ac86-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1ac86-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ac86-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ac86-120">E_FAIL</span></span>|<span data-ttu-id="1ac86-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1ac86-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ac86-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1ac86-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ac86-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ac86-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ac86-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ac86-124">Remarks</span></span>  
 <span data-ttu-id="1ac86-125">Wątki są przyznawane przetwarzania logowanie przy użyciu systemu okrężnego, który jest częściowo oparte na poziom priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="1ac86-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="1ac86-126">`SetPriority`Umożliwia CLR można ustawić ten poziom priorytetu wątku dla bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="1ac86-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="1ac86-127">Następujące `newPriority` wartości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1ac86-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="1ac86-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="1ac86-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="1ac86-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="1ac86-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="1ac86-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="1ac86-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="1ac86-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="1ac86-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="1ac86-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="1ac86-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="1ac86-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="1ac86-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="1ac86-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="1ac86-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="1ac86-135">Wywołania CLR `SetPriority` gdy wartość <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> jest modyfikowany przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1ac86-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="1ac86-136">Hosta można definiować własnych algorytmów przypisania priorytetu wątku i jest bezpłatna zignorowanie tego żądania.</span><span class="sxs-lookup"><span data-stu-id="1ac86-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ac86-137">`SetPriority`nie raportuje czy zmieniono poziom priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="1ac86-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="1ac86-138">Wywołanie [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) do określenia wartości poziom priorytetu wątku zadania.</span><span class="sxs-lookup"><span data-stu-id="1ac86-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="1ac86-139">Wartości poziom priorytetu wątku są definiowane przez Win32 `SetThreadPriority` funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ac86-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="1ac86-140">Aby uzyskać więcej informacji na temat priorytetu wątku zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1ac86-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ac86-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ac86-141">Requirements</span></span>  
 <span data-ttu-id="1ac86-142">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ac86-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac86-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ac86-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ac86-144">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ac86-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ac86-145">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac86-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac86-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ac86-146">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="1ac86-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ac86-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1ac86-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ac86-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1ac86-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ac86-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1ac86-150">GetPriority, metoda</span><span class="sxs-lookup"><span data-stu-id="1ac86-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [<span data-ttu-id="1ac86-151">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ac86-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
