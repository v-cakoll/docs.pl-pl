---
title: IHostTask::Join — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: dda68041dbf4efa82a35c48702d83aa231462fef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121375"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="a761a-102">IHostTask::Join — Metoda</span><span class="sxs-lookup"><span data-stu-id="a761a-102">IHostTask::Join Method</span></span>
<span data-ttu-id="a761a-103">Blokuje zadanie wywołujące do momentu zakończenia zadania reprezentowanego przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , upłynie określony przedział czasu lub [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a761a-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a761a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a761a-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a761a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a761a-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="a761a-106">podczas Interwał czasu (w milisekundach) oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="a761a-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="a761a-107">Jeśli ten interwał upłynie przed zakończeniem zadania, odblokowuje zadanie wywołujące.</span><span class="sxs-lookup"><span data-stu-id="a761a-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="a761a-108">podczas Jedna z wartości [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a761a-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="a761a-109">Wartość WAIT_ALERTABLE instruuje hosta, aby wznowić zadanie, jeśli `Alert` jest wywoływana przed upływem `milliseconds`.</span><span class="sxs-lookup"><span data-stu-id="a761a-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a761a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a761a-110">Return Value</span></span>  
  
|<span data-ttu-id="a761a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a761a-111">HRESULT</span></span>|<span data-ttu-id="a761a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a761a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a761a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a761a-113">S_OK</span></span>|<span data-ttu-id="a761a-114">`Join` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a761a-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="a761a-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a761a-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a761a-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a761a-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a761a-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a761a-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a761a-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a761a-118">The call timed out.</span></span>|  
|<span data-ttu-id="a761a-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a761a-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a761a-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a761a-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a761a-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a761a-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a761a-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna albo bieżące wystąpienie `IHostTask` nie jest skojarzone z zadaniem.</span><span class="sxs-lookup"><span data-stu-id="a761a-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="a761a-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a761a-123">E_FAIL</span></span>|<span data-ttu-id="a761a-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a761a-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a761a-125">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a761a-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a761a-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a761a-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a761a-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a761a-127">Requirements</span></span>  
 <span data-ttu-id="a761a-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a761a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a761a-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a761a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a761a-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a761a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a761a-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a761a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a761a-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a761a-132">See also</span></span>

- [<span data-ttu-id="a761a-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a761a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a761a-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a761a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a761a-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a761a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a761a-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a761a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="a761a-137">WAIT_OPTION, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a761a-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
