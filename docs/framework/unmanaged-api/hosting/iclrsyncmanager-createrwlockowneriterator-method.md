---
title: ICLRSyncManager::CreateRWLockOwnerIterator — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2b9c2fb2a4ddcc39c7690d832a94d772e8b82a3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497083"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="03c97-102">ICLRSyncManager::CreateRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="03c97-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="03c97-103">Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) Utwórz iterator dla hosta na potrzeby określania zestawu zadań, oczekiwania na blokadę zapisu czytnika.</span><span class="sxs-lookup"><span data-stu-id="03c97-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03c97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03c97-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03c97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03c97-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="03c97-106">[in] Plik cookie skojarzonego z blokadą żądany czytnik składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="03c97-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="03c97-107">[out] Wskaźnik do iteratora, który może być przekazywany do [getrwlockownernext —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) i [deleterwlockowneriterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="03c97-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03c97-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03c97-108">Return Value</span></span>  
  
|<span data-ttu-id="03c97-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03c97-109">HRESULT</span></span>|<span data-ttu-id="03c97-110">Opis</span><span class="sxs-lookup"><span data-stu-id="03c97-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03c97-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="03c97-111">S_OK</span></span>|<span data-ttu-id="03c97-112">`CreateRWLockOwnerIterator` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="03c97-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="03c97-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03c97-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03c97-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="03c97-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03c97-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03c97-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03c97-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="03c97-116">The call timed out.</span></span>|  
|<span data-ttu-id="03c97-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03c97-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03c97-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="03c97-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03c97-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03c97-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03c97-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="03c97-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03c97-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03c97-121">E_FAIL</span></span>|<span data-ttu-id="03c97-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="03c97-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03c97-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="03c97-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03c97-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="03c97-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="03c97-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="03c97-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="03c97-126">`CreateRWLockOwnerIterator` został wywołany w wątku, który jest obecnie uruchomiona kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="03c97-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03c97-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03c97-127">Remarks</span></span>  
 <span data-ttu-id="03c97-128">Hosty zwykle wywołują `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, i `GetRWLockOwnerNext` metody podczas wykrywania zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="03c97-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="03c97-129">Host jest odpowiedzialny za zapewnienie, że czytnik blokadę jest nadal ważny, CLR sprawia, że próba podtrzymywania czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="03c97-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="03c97-130">Kilka strategii są dostępne dla hosta zapewnić poprawność blokady:</span><span class="sxs-lookup"><span data-stu-id="03c97-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="03c97-131">Hosta można zablokować wywołań wersji na blokadę reader (na przykład [ihostsemaphore::releasesemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) przy jednoczesnym zapewnieniu, że ten blok nie spowoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="03c97-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="03c97-132">Host może zablokować opuszczenia oczekiwanie na obiekt zdarzenia skojarzone z czytnika blokadę ponownie zapewnienie, że ten blok nie spowoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="03c97-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03c97-133">`CreateRWLockOwnerIterator` musi zostać wywołany tylko na wątki, które są aktualnie wykonuje kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="03c97-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03c97-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03c97-134">Requirements</span></span>  
 <span data-ttu-id="03c97-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03c97-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03c97-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03c97-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03c97-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03c97-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03c97-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03c97-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c97-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03c97-139">See also</span></span>
- [<span data-ttu-id="03c97-140">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="03c97-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="03c97-141">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="03c97-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
