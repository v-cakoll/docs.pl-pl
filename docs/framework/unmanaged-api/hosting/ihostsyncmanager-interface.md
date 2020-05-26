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
ms.openlocfilehash: e96492270c403f93687245cee8b680dc16b3c787
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803123"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="d3f7c-102">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3f7c-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="d3f7c-103">Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do tworzenia pierwotnych synchronizacji przez wywołanie hosta zamiast korzystania z funkcji synchronizacji Win32.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3f7c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d3f7c-104">Methods</span></span>  
  
|<span data-ttu-id="d3f7c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-105">Method</span></span>|<span data-ttu-id="d3f7c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d3f7c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3f7c-107">CreateAutoEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="d3f7c-108">Tworzy obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="d3f7c-109">CreateCrst, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="d3f7c-110">Tworzy obiekt sekcji krytycznej do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="d3f7c-111">CreateCrstWithSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="d3f7c-112">Tworzy obiekt sekcji krytycznej z liczbą wirowania do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="d3f7c-113">CreateManualEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="d3f7c-114">Tworzy obiekt zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="d3f7c-115">CreateMonitorEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="d3f7c-116">Tworzy monitorowany obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="d3f7c-117">CreateRWLockReaderEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="d3f7c-118">Tworzy obiekt zdarzenia resetowania ręcznego dla implementacji blokady czytnika.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="d3f7c-119">CreateRWLockWriterEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="d3f7c-120">Tworzy obiekt zdarzenia autoresetowania dla implementacji blokady składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="d3f7c-121">CreateSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="d3f7c-122">Tworzy obiekt [IHostSemaphore](ihostsemaphore-interface.md) dla środowiska CLR do użycia jako semafor dla zdarzeń oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="d3f7c-123">SetCLRSyncManager, metoda</span><span class="sxs-lookup"><span data-stu-id="d3f7c-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="d3f7c-124">Ustawia wystąpienie [ICLRSyncManager](iclrsyncmanager-interface.md) do skojarzenia z bieżącym `IHostSyncManager` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3f7c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3f7c-125">Remarks</span></span>  
 <span data-ttu-id="d3f7c-126">Środowisko CLR wykrywa implementację hosta `IHostSyncManager` przez wywołanie metody [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) z `IID` IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="d3f7c-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3f7c-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3f7c-127">Requirements</span></span>  
 <span data-ttu-id="d3f7c-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f7c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f7c-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3f7c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3f7c-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3f7c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3f7c-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f7c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f7c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3f7c-132">See also</span></span>

- [<span data-ttu-id="d3f7c-133">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3f7c-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d3f7c-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d3f7c-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
