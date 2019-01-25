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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f4e25cfabbf18a9f0733d245259d9bb8f9c7757
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715557"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="53f8d-102">ICLRTask::Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="53f8d-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="53f8d-103">Informuje środowisko uruchomieniowe języka wspólnego (CLR), hosta zostało zakończone zadania i umożliwia CLR do ponownego użycia bieżącego [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia do reprezentowania inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="53f8d-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53f8d-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53f8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53f8d-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="53f8d-106">[in] `true`, jeśli środowisko wykonawcze zresetować wszystkie wątku statyczne wartościom oprócz zabezpieczeń i ustawień regionalnych informacji powiązanych z bieżącym `ICLRTask` wystąpienia; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="53f8d-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="53f8d-107">Jeśli wartość jest `true`, środowisko uruchomieniowe przywraca dane, które są przechowywane przy użyciu <xref:System.Threading.Thread.AllocateDataSlot%2A> lub <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="53f8d-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53f8d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53f8d-108">Return Value</span></span>  
  
|<span data-ttu-id="53f8d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53f8d-109">HRESULT</span></span>|<span data-ttu-id="53f8d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="53f8d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53f8d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53f8d-111">S_OK</span></span>|<span data-ttu-id="53f8d-112">`Reset` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="53f8d-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="53f8d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53f8d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53f8d-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetwarzania wywołania.</span><span class="sxs-lookup"><span data-stu-id="53f8d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="53f8d-115">pomyślnie</span><span class="sxs-lookup"><span data-stu-id="53f8d-115">successfully</span></span>|  
|<span data-ttu-id="53f8d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53f8d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53f8d-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="53f8d-117">The call timed out.</span></span>|  
|<span data-ttu-id="53f8d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53f8d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53f8d-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="53f8d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53f8d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53f8d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53f8d-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="53f8d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53f8d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53f8d-122">E_FAIL</span></span>|<span data-ttu-id="53f8d-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="53f8d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53f8d-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="53f8d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53f8d-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53f8d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53f8d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53f8d-126">Remarks</span></span>  
 <span data-ttu-id="53f8d-127">Środowisko CLR można odzyskać utworzone wcześniej `ICLRTask` wystąpienia, aby uniknąć zadań wielokrotnie tworzenia nowych wystąpień za każdym razem, gdy potrzebuje zadanie od nowa.</span><span class="sxs-lookup"><span data-stu-id="53f8d-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="53f8d-128">Host oferuje tę funkcję, wywołując `ICLRTask::Reset` zamiast [iclrtask::exittask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="53f8d-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="53f8d-129">Poniższa lista zawiera podsumowanie cyklu życia normalne `ICLRTask` wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="53f8d-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="53f8d-130">Środowisko uruchomieniowe tworzy nową `ICLRTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="53f8d-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="53f8d-131">Środowisko uruchomieniowe wywołuje [ihosttaskmanager::getcurrenttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) można pobrać odwołania do bieżącego zadania hosta.</span><span class="sxs-lookup"><span data-stu-id="53f8d-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="53f8d-132">Środowisko uruchomieniowe wywołuje [ihosttask::setclrtask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) Aby skojarzyć nowe wystąpienie z zadaniem hosta.</span><span class="sxs-lookup"><span data-stu-id="53f8d-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="53f8d-133">Zadanie wykonuje i kończy.</span><span class="sxs-lookup"><span data-stu-id="53f8d-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="53f8d-134">Host niszczy zadania, wywołując `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="53f8d-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="53f8d-135">`Reset` Zmienia tego scenariusza na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="53f8d-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="53f8d-136">W kroku 5 powyżej wywołania hosta `Reset` zresetować zadania do stanu czystego i następnie oddziela `ICLRTask` wystąpienia związanych z nią [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="53f8d-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="53f8d-137">Jeśli to konieczne, można buforować hosta `IHostTask` wystąpienia do ponownego wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="53f8d-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="53f8d-138">W kroku 1 powyżej, środowisko uruchomieniowe ściąga odtwarzania `ICLRTask` z pamięci podręcznej, zamiast tworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="53f8d-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="53f8d-139">To podejście działa dobrze w przypadku, gdy host ma też puli zadania procesu roboczego wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="53f8d-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="53f8d-140">Gdy host niszczy, jeden z jego `IHostTask` wystąpień niszczy, odpowiedni `ICLRTask` przez wywołanie metody `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="53f8d-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53f8d-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53f8d-141">Requirements</span></span>  
 <span data-ttu-id="53f8d-142">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53f8d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53f8d-143">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53f8d-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53f8d-144">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53f8d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53f8d-145">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53f8d-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f8d-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53f8d-146">See also</span></span>
- [<span data-ttu-id="53f8d-147">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="53f8d-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="53f8d-148">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="53f8d-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="53f8d-149">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="53f8d-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="53f8d-150">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="53f8d-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
