---
title: IHostSyncManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132628"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="5aebb-102">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5aebb-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="5aebb-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do tworzenia pierwotnych synchronizacji przez wywołanie hosta zamiast korzystania z funkcji synchronizacji Win32.</span><span class="sxs-lookup"><span data-stu-id="5aebb-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5aebb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5aebb-104">Methods</span></span>  
  
|<span data-ttu-id="5aebb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-105">Method</span></span>|<span data-ttu-id="5aebb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5aebb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5aebb-107">CreateAutoEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="5aebb-108">Tworzy obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="5aebb-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="5aebb-109">CreateCrst, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="5aebb-110">Tworzy obiekt sekcji krytycznej do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="5aebb-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="5aebb-111">CreateCrstWithSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="5aebb-112">Tworzy obiekt sekcji krytycznej z liczbą wirowania do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="5aebb-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="5aebb-113">CreateManualEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="5aebb-114">Tworzy obiekt zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="5aebb-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="5aebb-115">CreateMonitorEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="5aebb-116">Tworzy monitorowany obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="5aebb-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="5aebb-117">CreateRWLockReaderEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="5aebb-118">Tworzy obiekt zdarzenia resetowania ręcznego dla implementacji blokady czytnika.</span><span class="sxs-lookup"><span data-stu-id="5aebb-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="5aebb-119">CreateRWLockWriterEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="5aebb-120">Tworzy obiekt zdarzenia autoresetowania dla implementacji blokady składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="5aebb-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="5aebb-121">CreateSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="5aebb-122">Tworzy obiekt [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) dla środowiska CLR do użycia jako semafor dla zdarzeń oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5aebb-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="5aebb-123">SetCLRSyncManager, metoda</span><span class="sxs-lookup"><span data-stu-id="5aebb-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="5aebb-124">Ustawia wystąpienie [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) do skojarzenia z bieżącym wystąpieniem `IHostSyncManager`.</span><span class="sxs-lookup"><span data-stu-id="5aebb-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aebb-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5aebb-125">Remarks</span></span>  
 <span data-ttu-id="5aebb-126">Środowisko CLR wykrywa implementację `IHostSyncManager` hosta, wywołując metodę [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) z `IID`ą IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="5aebb-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aebb-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5aebb-127">Requirements</span></span>  
 <span data-ttu-id="5aebb-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aebb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aebb-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5aebb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5aebb-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5aebb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5aebb-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aebb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aebb-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5aebb-132">See also</span></span>

- [<span data-ttu-id="5aebb-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5aebb-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5aebb-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5aebb-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
