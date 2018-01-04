---
title: "ICLRTask::Reset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dc37f47fc01d73ff499ef974a2e11345a95286a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="bb7d9-102">ICLRTask::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb7d9-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="bb7d9-103">Informuje o środowisko uruchomieniowe języka wspólnego (CLR) została ukończona zadania hosta i umożliwia CLR do ponownego użycia bieżącego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienie do reprezentowania inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb7d9-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb7d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb7d9-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="bb7d9-106">[in] `true`, jeśli środowisko uruchomieniowe powinni resetować wszystkie wątku statyczne wartości dotyczące zabezpieczeń i ustawień regionalnych informacji powiązanych z bieżącym `ICLRTask` wystąpienia; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="bb7d9-107">Jeśli wartość jest `true`, środowisko uruchomieniowe resetuje danych, które były przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb7d9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb7d9-108">Return Value</span></span>  
  
|<span data-ttu-id="bb7d9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb7d9-109">HRESULT</span></span>|<span data-ttu-id="bb7d9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bb7d9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb7d9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb7d9-111">S_OK</span></span>|<span data-ttu-id="bb7d9-112">`Reset`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="bb7d9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb7d9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb7d9-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub przetwarzania wywołania.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="bb7d9-115">pomyślnie</span><span class="sxs-lookup"><span data-stu-id="bb7d9-115">successfully</span></span>|  
|<span data-ttu-id="bb7d9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb7d9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb7d9-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-117">The call timed out.</span></span>|  
|<span data-ttu-id="bb7d9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb7d9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb7d9-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb7d9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb7d9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb7d9-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb7d9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb7d9-122">E_FAIL</span></span>|<span data-ttu-id="bb7d9-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb7d9-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb7d9-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb7d9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb7d9-126">Remarks</span></span>  
 <span data-ttu-id="bb7d9-127">Środowisko CLR można odtworzyć wcześniej utworzony `ICLRTask` instancje, aby uniknąć zadań wielokrotnie tworzenia nowych wystąpień każdej próbie jej nowego zadania.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="bb7d9-128">Host umożliwia tej funkcji, wywołując `ICLRTask::Reset` zamiast [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="bb7d9-129">Poniższa lista zawiera podsumowanie normalnego cyklu życia `ICLRTask` wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="bb7d9-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="bb7d9-130">Tworzy nowe środowisko uruchomieniowe `ICLRTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="bb7d9-131">Wywołania środowiska uruchomieniowego [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) Aby pobrać odwołanie do bieżącego zadania hosta.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="bb7d9-132">Wywołania środowiska uruchomieniowego [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) Aby skojarzyć nowe wystąpienie z hosta zadań.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="bb7d9-133">Zadania wykonuje i kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="bb7d9-134">Host niszczy zadania, wywołując `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="bb7d9-135">`Reset`Zmienia tego scenariusza na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="bb7d9-136">W kroku 5 powyżej wywołania hosta `Reset` zresetować zadania do stanu czystego, a następnie oddziela `ICLRTask` wystąpienie z jego skojarzony [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="bb7d9-137">W razie potrzeby można buforować hosta `IHostTask` wystąpienie do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="bb7d9-138">W kroku 1 powyżej, środowisko uruchomieniowe ściąga odtwarzania `ICLRTask` z pamięci podręcznej, zamiast tworzyć nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="bb7d9-139">Takie podejście dobrze działa w przypadku hosta ma również pulą zadania procesu roboczego do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="bb7d9-140">Gdy host niszczy jednego z jego `IHostTask` wystąpień, niszczy, odpowiadającego `ICLRTask` przez wywołanie metody `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="bb7d9-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7d9-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb7d9-141">Requirements</span></span>  
 <span data-ttu-id="bb7d9-142">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb7d9-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb7d9-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb7d9-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb7d9-144">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb7d9-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb7d9-145">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb7d9-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb7d9-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb7d9-146">See Also</span></span>  
 [<span data-ttu-id="bb7d9-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb7d9-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="bb7d9-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb7d9-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="bb7d9-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb7d9-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="bb7d9-150">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb7d9-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
