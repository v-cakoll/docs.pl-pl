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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769632"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="1882b-102">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1882b-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="1882b-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do tworzenia podstawowych synchronizacji przez wywołanie metody hosta, zamiast korzystać z funkcji synchronizacji systemu Win32.</span><span class="sxs-lookup"><span data-stu-id="1882b-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1882b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1882b-104">Methods</span></span>  
  
|<span data-ttu-id="1882b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-105">Method</span></span>|<span data-ttu-id="1882b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1882b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1882b-107">CreateAutoEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="1882b-108">Tworzy obiekt zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="1882b-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="1882b-109">CreateCrst, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="1882b-110">Tworzy obiekt sekcję krytyczną synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="1882b-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="1882b-111">CreateCrstWithSpinCount, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="1882b-112">Tworzy obiekt sekcję krytyczną z liczbą pokrętła do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="1882b-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="1882b-113">CreateManualEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="1882b-114">Tworzy obiekt zdarzenie resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="1882b-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="1882b-115">CreateMonitorEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="1882b-116">Tworzy obiekt monitorowanych zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="1882b-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="1882b-117">CreateRWLockReaderEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="1882b-118">Tworzy obiekt zdarzeniach, resetowanego ręcznie do wykonania blokadę.</span><span class="sxs-lookup"><span data-stu-id="1882b-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="1882b-119">CreateRWLockWriterEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="1882b-120">Tworzy obiekt zdarzenie z resetowaniem automatycznym do wykonania blokadę.</span><span class="sxs-lookup"><span data-stu-id="1882b-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="1882b-121">CreateSemaphore, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="1882b-122">Tworzy [ihostsemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) obiektu CLR do użycia jako semafor dla zdarzeń oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="1882b-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="1882b-123">SetCLRSyncManager, metoda</span><span class="sxs-lookup"><span data-stu-id="1882b-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="1882b-124">Zestawy [iclrsyncmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) wystąpienia do skojarzenia z bieżącego `IHostSyncManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1882b-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1882b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1882b-125">Remarks</span></span>  
 <span data-ttu-id="1882b-126">Środowisko CLR wykryje wdrożenia hosta `IHostSyncManager` przez wywołanie metody [ihostcontrol::gethostmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metody z `IID` z IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="1882b-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1882b-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1882b-127">Requirements</span></span>  
 <span data-ttu-id="1882b-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1882b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1882b-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1882b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1882b-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1882b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1882b-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1882b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1882b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1882b-132">See also</span></span>

- [<span data-ttu-id="1882b-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1882b-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="1882b-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1882b-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
