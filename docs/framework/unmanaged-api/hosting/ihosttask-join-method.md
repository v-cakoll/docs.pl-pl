---
title: "IHostTask::Join — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Join
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85ee44fe9185364a6870b996ca98cfe6cc297bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="0fc37-102">IHostTask::Join — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fc37-102">IHostTask::Join Method</span></span>
<span data-ttu-id="0fc37-103">Blokuje wywoływania zadań dopóki reprezentowany przez bieżące zadanie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) zakończeniu wystąpienia, upłynie określony interwał, lub [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="0fc37-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fc37-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fc37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fc37-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="0fc37-106">[in] Przedział czasu (w milisekundach) oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="0fc37-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="0fc37-107">Jeśli ten interwał musi upłynąć, zanim kończy zadanie, odblokowuje wywoływania zadań.</span><span class="sxs-lookup"><span data-stu-id="0fc37-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="0fc37-108">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="0fc37-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="0fc37-109">Wartość WAIT_ALERTABLE powoduje, że host wznawiania zadania, jeśli `Alert` jest wywoływana przed `milliseconds` upływa.</span><span class="sxs-lookup"><span data-stu-id="0fc37-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fc37-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0fc37-110">Return Value</span></span>  
  
|<span data-ttu-id="0fc37-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fc37-111">HRESULT</span></span>|<span data-ttu-id="0fc37-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0fc37-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fc37-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fc37-113">S_OK</span></span>|<span data-ttu-id="0fc37-114">`Join`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0fc37-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="0fc37-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0fc37-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0fc37-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0fc37-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0fc37-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0fc37-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0fc37-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0fc37-118">The call timed out.</span></span>|  
|<span data-ttu-id="0fc37-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0fc37-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0fc37-120">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0fc37-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0fc37-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0fc37-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0fc37-122">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał lub bieżący `IHostTask` wystąpienia nie jest skojarzony z zadaniem.</span><span class="sxs-lookup"><span data-stu-id="0fc37-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="0fc37-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0fc37-123">E_FAIL</span></span>|<span data-ttu-id="0fc37-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0fc37-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0fc37-125">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0fc37-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0fc37-126">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0fc37-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fc37-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fc37-127">Requirements</span></span>  
 <span data-ttu-id="0fc37-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fc37-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fc37-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0fc37-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0fc37-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fc37-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fc37-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fc37-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc37-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fc37-132">See Also</span></span>  
 [<span data-ttu-id="0fc37-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fc37-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0fc37-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fc37-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0fc37-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fc37-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0fc37-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fc37-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="0fc37-137">WAIT_OPTION, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0fc37-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
