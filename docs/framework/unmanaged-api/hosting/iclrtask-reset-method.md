---
title: ICLRTask::Reset — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124644"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="837a3-102">ICLRTask::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="837a3-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="837a3-103">Informuje środowisko uruchomieniowe języka wspólnego (CLR), że host ukończył zadanie, i włącza środowisko CLR do ponownego użycia bieżącego wystąpienia [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) , aby reprezentować inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="837a3-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="837a3-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="837a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="837a3-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="837a3-106">[in] `true`, jeśli środowisko uruchomieniowe powinno zresetować wszystkie wartości statyczne powiązane z wątkiem oprócz informacji o zabezpieczeniach i ustawieniach regionalnych związanych z bieżącym wystąpieniem `ICLRTask`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="837a3-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="837a3-107">Jeśli wartość jest `true`, środowisko uruchomieniowe resetuje dane przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="837a3-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="837a3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="837a3-108">Return Value</span></span>  
  
|<span data-ttu-id="837a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="837a3-109">HRESULT</span></span>|<span data-ttu-id="837a3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="837a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="837a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="837a3-111">S_OK</span></span>|<span data-ttu-id="837a3-112">`Reset` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="837a3-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="837a3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="837a3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="837a3-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="837a3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="837a3-115">została</span><span class="sxs-lookup"><span data-stu-id="837a3-115">successfully</span></span>|  
|<span data-ttu-id="837a3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="837a3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="837a3-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="837a3-117">The call timed out.</span></span>|  
|<span data-ttu-id="837a3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="837a3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="837a3-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="837a3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="837a3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="837a3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="837a3-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="837a3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="837a3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="837a3-122">E_FAIL</span></span>|<span data-ttu-id="837a3-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="837a3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="837a3-124">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="837a3-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="837a3-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="837a3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="837a3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="837a3-126">Remarks</span></span>  
 <span data-ttu-id="837a3-127">Środowisko CLR może odtworzyć wcześniej utworzone wystąpienia `ICLRTask`, aby uniknąć narzutu wielokrotnego tworzenia nowych wystąpień za każdym razem, gdy potrzebne jest nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="837a3-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="837a3-128">Host włącza tę funkcję, wywołując `ICLRTask::Reset` zamiast [ICLRTask:: ExitTask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po ukończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="837a3-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="837a3-129">Poniższa lista podsumowuje normalny cykl życia wystąpienia `ICLRTask`:</span><span class="sxs-lookup"><span data-stu-id="837a3-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="837a3-130">Środowisko uruchomieniowe tworzy nowe wystąpienie `ICLRTask`.</span><span class="sxs-lookup"><span data-stu-id="837a3-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="837a3-131">Wywołania środowiska uruchomieniowego [IHostTaskManager:: GetCurrentTask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) w celu uzyskania odwołania do bieżącego zadania hosta.</span><span class="sxs-lookup"><span data-stu-id="837a3-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="837a3-132">Wywołania środowiska uruchomieniowego [IHostTask:: SetCLRTask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) w celu skojarzenia nowego wystąpienia z zadaniem hosta.</span><span class="sxs-lookup"><span data-stu-id="837a3-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="837a3-133">Zadanie jest wykonywane i uzupełniane.</span><span class="sxs-lookup"><span data-stu-id="837a3-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="837a3-134">Host niszczy zadanie, wywołując `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="837a3-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="837a3-135">`Reset` zmienić ten scenariusz na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="837a3-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="837a3-136">W kroku 5 powyżej, Host wywołuje `Reset` Resetowanie zadania do stanu czystego, a następnie oddziela wystąpienie `ICLRTask` od skojarzonego z nim wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="837a3-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="837a3-137">W razie potrzeby host może również buforować wystąpienie `IHostTask` w celu ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="837a3-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="837a3-138">W kroku 1 środowisko uruchomieniowe pobiera `ICLRTask` odtwarzania z pamięci podręcznej, zamiast tworzyć nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="837a3-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="837a3-139">Takie podejście działa prawidłowo, gdy host ma również pulę zadań wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="837a3-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="837a3-140">Gdy host niszczy jeden z jego `IHostTask` wystąpień, niszczy odpowiednie `ICLRTask` przez wywołanie `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="837a3-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837a3-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="837a3-141">Requirements</span></span>  
 <span data-ttu-id="837a3-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="837a3-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837a3-143">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="837a3-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="837a3-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="837a3-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="837a3-145">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837a3-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837a3-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="837a3-146">See also</span></span>

- [<span data-ttu-id="837a3-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="837a3-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="837a3-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="837a3-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="837a3-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="837a3-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="837a3-150">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="837a3-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
