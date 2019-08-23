---
title: IHostTask::Alert — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b3fc0b1dde35e743e699d22c5766cab4cf0faf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964718"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="802e3-102">IHostTask::Alert — Metoda</span><span class="sxs-lookup"><span data-stu-id="802e3-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="802e3-103">Żąda, aby Host wznowił zadanie reprezentowane przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , więc zadanie można przerwać.</span><span class="sxs-lookup"><span data-stu-id="802e3-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="802e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="802e3-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="802e3-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="802e3-105">Return Value</span></span>  
  
|<span data-ttu-id="802e3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="802e3-106">HRESULT</span></span>|<span data-ttu-id="802e3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="802e3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="802e3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="802e3-108">S_OK</span></span>|<span data-ttu-id="802e3-109">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="802e3-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="802e3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="802e3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="802e3-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="802e3-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="802e3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="802e3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="802e3-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="802e3-113">The call timed out.</span></span>|  
|<span data-ttu-id="802e3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="802e3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="802e3-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="802e3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="802e3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="802e3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="802e3-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="802e3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="802e3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="802e3-118">E_FAIL</span></span>|<span data-ttu-id="802e3-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="802e3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="802e3-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="802e3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="802e3-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="802e3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="802e3-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="802e3-122">Remarks</span></span>  
 <span data-ttu-id="802e3-123">Środowisko CLR wywołuje `Alert` metodę, gdy <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> jest wywoływana z <xref:System.AppDomain> kodu użytkownika lub gdy jest skojarzony z bieżącym <xref:System.Threading.Thread> zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="802e3-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="802e3-124">Host musi zwrócić natychmiast, ponieważ wywołanie zostało wykonane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="802e3-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="802e3-125">Jeśli host nie może natychmiast ostrzec zadania, musi wznowić działanie przy następnym wejściu w stan, w którym można otrzymywać alerty.</span><span class="sxs-lookup"><span data-stu-id="802e3-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="802e3-126">`Alert`ma wpływ tylko na te zadania, do których środowisko uruchomieniowe przekazało [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartość WAIT_ALERTABLE do metod takich jak [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="802e3-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="802e3-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="802e3-127">Requirements</span></span>  
 <span data-ttu-id="802e3-128">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="802e3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="802e3-129">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="802e3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="802e3-130">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="802e3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="802e3-131">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="802e3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802e3-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="802e3-132">See also</span></span>

- [<span data-ttu-id="802e3-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="802e3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="802e3-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="802e3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="802e3-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="802e3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="802e3-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="802e3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
