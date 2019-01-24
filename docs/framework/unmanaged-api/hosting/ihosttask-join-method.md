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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f404fef10f83dac8938953e29b233d3a01135559
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547348"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="37f79-102">IHostTask::Join — Metoda</span><span class="sxs-lookup"><span data-stu-id="37f79-102">IHostTask::Join Method</span></span>
<span data-ttu-id="37f79-103">Blokuje wywołującym je zadaniem i do zadań, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) ukończenia wystąpienia, przez określony interwał czasu upłynie, lub [ihosttask::alert —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="37f79-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37f79-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37f79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37f79-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="37f79-106">[in] Interwał czasu (w milisekundach) oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="37f79-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="37f79-107">Jeśli ten interwał musi upłynąć, zanim zadanie kończy działanie, odblokowuje wywołującym je zadaniem.</span><span class="sxs-lookup"><span data-stu-id="37f79-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="37f79-108">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="37f79-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="37f79-109">Wartość WAIT_ALERTABLE powoduje, że host wznawiania zadania, jeśli `Alert` jest wywoływana przed `milliseconds` upływa.</span><span class="sxs-lookup"><span data-stu-id="37f79-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37f79-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37f79-110">Return Value</span></span>  
  
|<span data-ttu-id="37f79-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37f79-111">HRESULT</span></span>|<span data-ttu-id="37f79-112">Opis</span><span class="sxs-lookup"><span data-stu-id="37f79-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37f79-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="37f79-113">S_OK</span></span>|<span data-ttu-id="37f79-114">`Join` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="37f79-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="37f79-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37f79-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37f79-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="37f79-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37f79-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37f79-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37f79-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="37f79-118">The call timed out.</span></span>|  
|<span data-ttu-id="37f79-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37f79-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37f79-120">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="37f79-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37f79-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37f79-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37f79-122">Zdarzenie zostało anulowane podczas blokowania wątku lub włókna oczekiwał na lub bieżącego `IHostTask` wystąpienia nie jest skojarzona z zadaniem.</span><span class="sxs-lookup"><span data-stu-id="37f79-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="37f79-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37f79-123">E_FAIL</span></span>|<span data-ttu-id="37f79-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="37f79-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37f79-125">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="37f79-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37f79-126">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37f79-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37f79-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37f79-127">Requirements</span></span>  
 <span data-ttu-id="37f79-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f79-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f79-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37f79-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37f79-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37f79-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37f79-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37f79-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f79-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37f79-132">See also</span></span>
- [<span data-ttu-id="37f79-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="37f79-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="37f79-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="37f79-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="37f79-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="37f79-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="37f79-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="37f79-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="37f79-137">WAIT_OPTION, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="37f79-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
