---
title: IHostGCManager::SuspensionStarting — Metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ef5bb2539820d5a7bcd4ca6b4de86564290709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984415"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="d1448-102">IHostGCManager::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1448-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="d1448-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje wykonywanie zadań do wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d1448-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1448-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1448-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d1448-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1448-105">Return Value</span></span>  
  
|<span data-ttu-id="d1448-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1448-106">HRESULT</span></span>|<span data-ttu-id="d1448-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d1448-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1448-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1448-108">S_OK</span></span>|<span data-ttu-id="d1448-109">`SuspensionStarting` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d1448-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="d1448-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1448-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1448-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d1448-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1448-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1448-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1448-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d1448-113">The call timed out.</span></span>|  
|<span data-ttu-id="d1448-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1448-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1448-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d1448-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1448-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1448-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1448-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d1448-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1448-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1448-118">E_FAIL</span></span>|<span data-ttu-id="d1448-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d1448-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1448-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d1448-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1448-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1448-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1448-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1448-122">Remarks</span></span>  
 <span data-ttu-id="d1448-123">CLR wywołuje `SuspensionStarting` poinformować hosta, który odbywa się wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d1448-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1448-124">Nie harmonogram tego zadania.</span><span class="sxs-lookup"><span data-stu-id="d1448-124">Do not reschedule this task.</span></span> <span data-ttu-id="d1448-125">Host musi zmienić harmonogram zadania podczas [threadisblockingforsuspension —](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d1448-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1448-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1448-126">Requirements</span></span>  
 <span data-ttu-id="d1448-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1448-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1448-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1448-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1448-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1448-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1448-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1448-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1448-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1448-131">See also</span></span>

- [<span data-ttu-id="d1448-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1448-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d1448-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1448-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d1448-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1448-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d1448-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1448-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="d1448-136">IHostGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1448-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
