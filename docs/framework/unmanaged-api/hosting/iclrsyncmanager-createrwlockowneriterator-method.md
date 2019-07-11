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
ms.openlocfilehash: 1951efecca6c81322c3a0753eaaf06e9651e3d39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759152"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="11d9a-102">ICLRSyncManager::CreateRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="11d9a-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="11d9a-103">Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) Utwórz iterator dla hosta na potrzeby określania zestawu zadań, oczekiwania na blokadę zapisu czytnika.</span><span class="sxs-lookup"><span data-stu-id="11d9a-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11d9a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11d9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11d9a-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="11d9a-106">[in] Plik cookie skojarzonego z blokadą żądany czytnik składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="11d9a-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="11d9a-107">[out] Wskaźnik do iteratora, który może być przekazywany do [getrwlockownernext —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) i [deleterwlockowneriterator —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="11d9a-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11d9a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11d9a-108">Return Value</span></span>  
  
|<span data-ttu-id="11d9a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11d9a-109">HRESULT</span></span>|<span data-ttu-id="11d9a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="11d9a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11d9a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="11d9a-111">S_OK</span></span>|<span data-ttu-id="11d9a-112">`CreateRWLockOwnerIterator` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="11d9a-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="11d9a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11d9a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11d9a-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="11d9a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11d9a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11d9a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11d9a-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="11d9a-116">The call timed out.</span></span>|  
|<span data-ttu-id="11d9a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11d9a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11d9a-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="11d9a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11d9a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11d9a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11d9a-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="11d9a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11d9a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11d9a-121">E_FAIL</span></span>|<span data-ttu-id="11d9a-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11d9a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11d9a-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="11d9a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11d9a-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11d9a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11d9a-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="11d9a-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="11d9a-126">`CreateRWLockOwnerIterator` został wywołany w wątku, który jest obecnie uruchomiona kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="11d9a-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11d9a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11d9a-127">Remarks</span></span>  
 <span data-ttu-id="11d9a-128">Hosty zwykle wywołują `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, i `GetRWLockOwnerNext` metody podczas wykrywania zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="11d9a-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="11d9a-129">Host jest odpowiedzialny za zapewnienie, że czytnik blokadę jest nadal ważny, CLR sprawia, że próba podtrzymywania czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="11d9a-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="11d9a-130">Kilka strategii są dostępne dla hosta zapewnić poprawność blokady:</span><span class="sxs-lookup"><span data-stu-id="11d9a-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="11d9a-131">Hosta można zablokować wywołań wersji na blokadę reader (na przykład [ihostsemaphore::releasesemaphore —](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) przy jednoczesnym zapewnieniu, że ten blok nie spowoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="11d9a-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="11d9a-132">Host może zablokować opuszczenia oczekiwanie na obiekt zdarzenia skojarzone z czytnika blokadę ponownie zapewnienie, że ten blok nie spowoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="11d9a-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11d9a-133">`CreateRWLockOwnerIterator` musi zostać wywołany tylko na wątki, które są aktualnie wykonuje kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="11d9a-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d9a-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11d9a-134">Requirements</span></span>  
 <span data-ttu-id="11d9a-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11d9a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d9a-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11d9a-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11d9a-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11d9a-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11d9a-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11d9a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d9a-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11d9a-139">See also</span></span>

- [<span data-ttu-id="11d9a-140">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11d9a-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="11d9a-141">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11d9a-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
