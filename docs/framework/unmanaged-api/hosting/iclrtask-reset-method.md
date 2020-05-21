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
ms.openlocfilehash: 15004238ee296e44ae77cd8739b7f62ea2a7a100
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762971"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="78b6f-102">ICLRTask::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="78b6f-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="78b6f-103">Informuje środowisko uruchomieniowe języka wspólnego (CLR), że host ukończył zadanie, i włącza środowisko CLR do ponownego użycia bieżącego wystąpienia [ICLRTask](iclrtask-interface.md) , aby reprezentować inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="78b6f-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78b6f-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78b6f-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="78b6f-106">[in] `true` , jeśli środowisko uruchomieniowe powinno zresetować wszystkie wartości statyczne powiązane z wątkiem oprócz informacji o zabezpieczeniach i ustawieniach regionalnych związanych z bieżącym `ICLRTask` wystąpieniem; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="78b6f-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="78b6f-107">Jeśli wartość to `true` , środowisko uruchomieniowe resetuje dane przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .</span><span class="sxs-lookup"><span data-stu-id="78b6f-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78b6f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78b6f-108">Return Value</span></span>  
  
|<span data-ttu-id="78b6f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78b6f-109">HRESULT</span></span>|<span data-ttu-id="78b6f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="78b6f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78b6f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="78b6f-111">S_OK</span></span>|<span data-ttu-id="78b6f-112">`Reset`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="78b6f-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="78b6f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78b6f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78b6f-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="78b6f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="78b6f-115">została</span><span class="sxs-lookup"><span data-stu-id="78b6f-115">successfully</span></span>|  
|<span data-ttu-id="78b6f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78b6f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78b6f-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="78b6f-117">The call timed out.</span></span>|  
|<span data-ttu-id="78b6f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78b6f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78b6f-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="78b6f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78b6f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78b6f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78b6f-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="78b6f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78b6f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78b6f-122">E_FAIL</span></span>|<span data-ttu-id="78b6f-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="78b6f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78b6f-124">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="78b6f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78b6f-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78b6f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78b6f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78b6f-126">Remarks</span></span>  
 <span data-ttu-id="78b6f-127">Środowisko CLR może odtworzyć wcześniej utworzone `ICLRTask` wystąpienia, aby uniknąć narzutu wielokrotnego tworzenia nowych wystąpień za każdym razem, gdy potrzebne jest nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="78b6f-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="78b6f-128">Host włącza tę funkcję, wywołując `ICLRTask::Reset` zamiast [ICLRTask:: ExitTask —](iclrtask-exittask-method.md) , gdy ukończył zadanie.</span><span class="sxs-lookup"><span data-stu-id="78b6f-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="78b6f-129">Poniższa lista podsumowuje normalny cykl życia `ICLRTask` wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="78b6f-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="78b6f-130">Środowisko uruchomieniowe tworzy nowe `ICLRTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="78b6f-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="78b6f-131">Wywołania środowiska uruchomieniowego [IHostTaskManager:: GetCurrentTask —](ihosttaskmanager-getcurrenttask-method.md) w celu uzyskania odwołania do bieżącego zadania hosta.</span><span class="sxs-lookup"><span data-stu-id="78b6f-131">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="78b6f-132">Wywołania środowiska uruchomieniowego [IHostTask:: SetCLRTask —](ihosttask-setclrtask-method.md) w celu skojarzenia nowego wystąpienia z zadaniem hosta.</span><span class="sxs-lookup"><span data-stu-id="78b6f-132">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="78b6f-133">Zadanie jest wykonywane i uzupełniane.</span><span class="sxs-lookup"><span data-stu-id="78b6f-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="78b6f-134">Host niszczy zadanie, wywołując metodę `ICLRTask::ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="78b6f-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="78b6f-135">`Reset`zmienia ten scenariusz na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="78b6f-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="78b6f-136">W kroku 5 powyżej, Host wywołuje `Reset` w celu zresetowania zadania do stanu czystego, a następnie oddziela `ICLRTask` wystąpienie od skojarzonego z nim wystąpienia [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="78b6f-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="78b6f-137">Jeśli to konieczne, host może również buforować `IHostTask` wystąpienie do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="78b6f-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="78b6f-138">W kroku 1 środowisko uruchomieniowe pobierze ponownie `ICLRTask` z pamięci podręcznej, zamiast tworzyć nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="78b6f-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="78b6f-139">Takie podejście działa prawidłowo, gdy host ma również pulę zadań wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="78b6f-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="78b6f-140">Gdy host niszczy jedno z jego `IHostTask` wystąpień, niszczy odpowiednie `ICLRTask` wywołanie `ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="78b6f-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b6f-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78b6f-141">Requirements</span></span>  
 <span data-ttu-id="78b6f-142">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78b6f-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b6f-143">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="78b6f-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78b6f-144">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="78b6f-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78b6f-145">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78b6f-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b6f-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78b6f-146">See also</span></span>

- [<span data-ttu-id="78b6f-147">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="78b6f-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="78b6f-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="78b6f-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="78b6f-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="78b6f-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="78b6f-150">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="78b6f-150">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
