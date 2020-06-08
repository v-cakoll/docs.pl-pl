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
ms.openlocfilehash: fd3c941d89fbd93f30fc1af235f6310b23758973
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501459"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="119c8-102">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="119c8-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="119c8-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do tworzenia pierwotnych synchronizacji przez wywołanie hosta zamiast korzystania z funkcji synchronizacji Win32.</span><span class="sxs-lookup"><span data-stu-id="119c8-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="119c8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="119c8-104">Methods</span></span>  
  
|<span data-ttu-id="119c8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-105">Method</span></span>|<span data-ttu-id="119c8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="119c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="119c8-107">CreateAutoEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="119c8-108">Tworzy obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="119c8-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="119c8-109">CreateCrst, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="119c8-110">Tworzy obiekt sekcji krytycznej do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="119c8-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="119c8-111">CreateCrstWithSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="119c8-112">Tworzy obiekt sekcji krytycznej z liczbą wirowania do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="119c8-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="119c8-113">CreateManualEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="119c8-114">Tworzy obiekt zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="119c8-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="119c8-115">CreateMonitorEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="119c8-116">Tworzy monitorowany obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="119c8-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="119c8-117">CreateRWLockReaderEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="119c8-118">Tworzy obiekt zdarzenia resetowania ręcznego dla implementacji blokady czytnika.</span><span class="sxs-lookup"><span data-stu-id="119c8-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="119c8-119">CreateRWLockWriterEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="119c8-120">Tworzy obiekt zdarzenia autoresetowania dla implementacji blokady składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="119c8-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="119c8-121">CreateSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-121">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="119c8-122">Tworzy obiekt [IHostSemaphore](ihostsemaphore-interface.md) dla środowiska CLR do użycia jako semafor dla zdarzeń oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="119c8-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="119c8-123">SetCLRSyncManager, metoda</span><span class="sxs-lookup"><span data-stu-id="119c8-123">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="119c8-124">Ustawia wystąpienie [ICLRSyncManager](iclrsyncmanager-interface.md) do skojarzenia z bieżącym `IHostSyncManager` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="119c8-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="119c8-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="119c8-125">Remarks</span></span>  
 <span data-ttu-id="119c8-126">Środowisko CLR wykrywa implementację hosta `IHostSyncManager` przez wywołanie metody [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) z `IID` IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="119c8-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119c8-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="119c8-127">Requirements</span></span>  
 <span data-ttu-id="119c8-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119c8-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119c8-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="119c8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="119c8-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="119c8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="119c8-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119c8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119c8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="119c8-132">See also</span></span>

- [<span data-ttu-id="119c8-133">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="119c8-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="119c8-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="119c8-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
