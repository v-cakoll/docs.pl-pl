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
ms.openlocfilehash: b2fc1d6c45eb72410ccfa1071064aa1a31ae46e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121403"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="f5c37-102">IHostTask::Alert — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5c37-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="f5c37-103">Żąda, aby Host wznowił zadanie reprezentowane przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , więc zadanie można przerwać.</span><span class="sxs-lookup"><span data-stu-id="f5c37-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5c37-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f5c37-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5c37-105">Return Value</span></span>  
  
|<span data-ttu-id="f5c37-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5c37-106">HRESULT</span></span>|<span data-ttu-id="f5c37-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f5c37-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5c37-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5c37-108">S_OK</span></span>|<span data-ttu-id="f5c37-109">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="f5c37-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="f5c37-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5c37-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5c37-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f5c37-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5c37-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5c37-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5c37-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f5c37-113">The call timed out.</span></span>|  
|<span data-ttu-id="f5c37-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5c37-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5c37-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f5c37-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5c37-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5c37-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5c37-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f5c37-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5c37-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5c37-118">E_FAIL</span></span>|<span data-ttu-id="f5c37-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f5c37-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5c37-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f5c37-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5c37-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5c37-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5c37-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5c37-122">Remarks</span></span>  
 <span data-ttu-id="f5c37-123">Środowisko CLR wywołuje metodę `Alert`, gdy <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika lub gdy <xref:System.AppDomain> skojarzone z bieżącym <xref:System.Threading.Thread> zostaje zamknięty.</span><span class="sxs-lookup"><span data-stu-id="f5c37-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="f5c37-124">Host musi zwrócić natychmiast, ponieważ wywołanie zostało wykonane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f5c37-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="f5c37-125">Jeśli host nie może natychmiast ostrzec zadania, musi wznowić działanie przy następnym wejściu w stan, w którym można otrzymywać alerty.</span><span class="sxs-lookup"><span data-stu-id="f5c37-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5c37-126">`Alert` ma wpływ tylko na te zadania, do których środowisko uruchomieniowe przekazało [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartość WAIT_ALERTABLE do metod takich jak [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="f5c37-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c37-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5c37-127">Requirements</span></span>  
 <span data-ttu-id="f5c37-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c37-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c37-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5c37-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5c37-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5c37-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5c37-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c37-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c37-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5c37-132">See also</span></span>

- [<span data-ttu-id="f5c37-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c37-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f5c37-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c37-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f5c37-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c37-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f5c37-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5c37-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
