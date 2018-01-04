---
title: "IHostSyncManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="1746c-102">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1746c-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="1746c-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby utworzyć przez wywołanie metody hosta zamiast funkcji synchronizacji Win32 elementy podstawowe synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="1746c-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1746c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1746c-104">Methods</span></span>  
  
|<span data-ttu-id="1746c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-105">Method</span></span>|<span data-ttu-id="1746c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1746c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1746c-107">CreateAutoEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="1746c-108">Tworzy obiekt zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="1746c-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="1746c-109">CreateCrst, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="1746c-110">Tworzy obiekt sekcja krytyczna synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="1746c-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="1746c-111">CreateCrstWithSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="1746c-112">Tworzy obiekt sekcja krytyczna z licznikiem pokrętła do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="1746c-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="1746c-113">CreateManualEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="1746c-114">Tworzy obiekt zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="1746c-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="1746c-115">CreateMonitorEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="1746c-116">Tworzy obiekt monitorowanych zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="1746c-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="1746c-117">CreateRWLockReaderEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="1746c-118">Tworzy obiekt zdarzenia resetowania ręcznego wykonania blokadę.</span><span class="sxs-lookup"><span data-stu-id="1746c-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="1746c-119">CreateRWLockWriterEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="1746c-120">Tworzy obiekt zdarzenie z resetowaniem automatycznym dla implementacji blokadę.</span><span class="sxs-lookup"><span data-stu-id="1746c-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="1746c-121">CreateSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="1746c-122">Tworzy [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) obiektu CLR do użycia jako semafor Czekaj zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1746c-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="1746c-123">SetCLRSyncManager, metoda</span><span class="sxs-lookup"><span data-stu-id="1746c-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="1746c-124">Ustawia [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) wystąpienie do skojarzenia z bieżącym `IHostSyncManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1746c-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1746c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1746c-125">Remarks</span></span>  
 <span data-ttu-id="1746c-126">Środowisko CLR odnajduje implementacja hosta `IHostSyncManager` przez wywołanie metody [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metody z `IID` z IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="1746c-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1746c-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1746c-127">Requirements</span></span>  
 <span data-ttu-id="1746c-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1746c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1746c-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1746c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1746c-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1746c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1746c-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1746c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1746c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1746c-132">See Also</span></span>  
 [<span data-ttu-id="1746c-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1746c-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1746c-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1746c-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
