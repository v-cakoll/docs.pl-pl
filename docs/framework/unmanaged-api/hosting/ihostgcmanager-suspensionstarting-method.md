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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213093"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="dd875-102">IHostGCManager::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd875-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="dd875-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje wykonywanie zadań do wykonania wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dd875-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd875-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd875-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dd875-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd875-105">Return Value</span></span>  
  
|<span data-ttu-id="dd875-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd875-106">HRESULT</span></span>|<span data-ttu-id="dd875-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dd875-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd875-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd875-108">S_OK</span></span>|`SuspensionStarting` <span data-ttu-id="dd875-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="dd875-109">returned successfully.</span></span>|  
|<span data-ttu-id="dd875-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd875-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd875-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd875-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd875-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd875-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd875-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd875-113">The call timed out.</span></span>|  
|<span data-ttu-id="dd875-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd875-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd875-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="dd875-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd875-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd875-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd875-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="dd875-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd875-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd875-118">E_FAIL</span></span>|<span data-ttu-id="dd875-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dd875-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd875-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="dd875-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd875-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd875-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd875-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd875-122">Remarks</span></span>  
 <span data-ttu-id="dd875-123">CLR wywołuje `SuspensionStarting` poinformować hosta, który odbywa się wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dd875-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dd875-124">Nie harmonogram tego zadania.</span><span class="sxs-lookup"><span data-stu-id="dd875-124">Do not reschedule this task.</span></span> <span data-ttu-id="dd875-125">Host musi zmienić harmonogram zadania podczas [threadisblockingforsuspension —](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="dd875-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd875-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd875-126">Requirements</span></span>  
 <span data-ttu-id="dd875-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd875-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd875-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dd875-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd875-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd875-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dd875-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dd875-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd875-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd875-131">See also</span></span>

- [<span data-ttu-id="dd875-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd875-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dd875-133">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd875-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dd875-134">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd875-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dd875-135">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd875-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="dd875-136">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd875-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
