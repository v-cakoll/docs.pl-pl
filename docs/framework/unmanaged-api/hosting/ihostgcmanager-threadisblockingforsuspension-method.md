---
title: "IHostGCManager::ThreadIsBlockingForSuspension — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.ThreadIsBlockingForSuspension
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ea5f110754b8b607673bcbd4060dee85cd5ca9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="34790-102">IHostGCManager::ThreadIsBlockingForSuspension — Metoda</span><span class="sxs-lookup"><span data-stu-id="34790-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="34790-103">Powiadamia hosta, który jest wątków, z którego wykonano wywołanie metody informacje mają być blokowane dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="34790-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34790-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34790-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="34790-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34790-105">Return Value</span></span>  
  
|<span data-ttu-id="34790-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34790-106">HRESULT</span></span>|<span data-ttu-id="34790-107">Opis</span><span class="sxs-lookup"><span data-stu-id="34790-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34790-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="34790-108">S_OK</span></span>|<span data-ttu-id="34790-109">`ThreadIsBlockingForSuspension`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34790-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="34790-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34790-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34790-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="34790-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34790-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34790-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34790-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="34790-113">The call timed out.</span></span>|  
|<span data-ttu-id="34790-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34790-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34790-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="34790-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34790-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34790-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34790-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="34790-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34790-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34790-118">E_FAIL</span></span>|<span data-ttu-id="34790-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="34790-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34790-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="34790-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34790-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34790-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34790-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34790-122">Remarks</span></span>  
 <span data-ttu-id="34790-123">Zazwyczaj wymaga środowiska CLR `ThreadIsBlockForSuspension` metody w ramach przygotowania do pamięci, aby zapewnić możliwość zaplanować wątku niezarządzanego zadań hosta.</span><span class="sxs-lookup"><span data-stu-id="34790-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34790-124">Host może zmienić harmonogram zadań tylko po wywołaniu `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="34790-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="34790-125">Po wywołania środowiska uruchomieniowego [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), host nie ponowne planowanie zadania.</span><span class="sxs-lookup"><span data-stu-id="34790-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34790-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34790-126">Requirements</span></span>  
 <span data-ttu-id="34790-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34790-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34790-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34790-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34790-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34790-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34790-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34790-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34790-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34790-131">See Also</span></span>  
 [<span data-ttu-id="34790-132">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="34790-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="34790-133">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="34790-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="34790-134">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="34790-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="34790-135">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="34790-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="34790-136">IHostGCManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="34790-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
