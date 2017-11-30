---
title: "ICLRSyncManager::CreateRWLockOwnerIterator — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.CreateRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f153550544a8e7622ea3cec0273ff9a97a99f91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="a1f03-102">ICLRSyncManager::CreateRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1f03-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="a1f03-103">Żądania, które iteratora hosta na służy do określania zestawu zadań oczekujących na blokadę zapisu czytnika utworzyć środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a1f03-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1f03-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1f03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1f03-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a1f03-106">[in] Plik cookie skojarzone z żądaną czytnika zapisującym blokady.</span><span class="sxs-lookup"><span data-stu-id="a1f03-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="a1f03-107">[out] Wskaźnik do iterację mogą zostać przekazane do [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) i [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a1f03-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1f03-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1f03-108">Return Value</span></span>  
  
|<span data-ttu-id="a1f03-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1f03-109">HRESULT</span></span>|<span data-ttu-id="a1f03-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a1f03-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1f03-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1f03-111">S_OK</span></span>|<span data-ttu-id="a1f03-112">`CreateRWLockOwnerIterator`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1f03-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="a1f03-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1f03-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1f03-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a1f03-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1f03-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1f03-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1f03-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a1f03-116">The call timed out.</span></span>|  
|<span data-ttu-id="a1f03-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1f03-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1f03-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a1f03-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1f03-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1f03-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1f03-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a1f03-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1f03-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1f03-121">E_FAIL</span></span>|<span data-ttu-id="a1f03-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a1f03-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1f03-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a1f03-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1f03-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1f03-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a1f03-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a1f03-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a1f03-126">`CreateRWLockOwnerIterator`została wywołana w wątku, który jest obecnie uruchomiona kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a1f03-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1f03-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1f03-127">Remarks</span></span>  
 <span data-ttu-id="a1f03-128">Hosty zwykle wywołują `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, i `GetRWLockOwnerNext` metod wykrywania zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a1f03-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="a1f03-129">Host jest odpowiedzialny za zapewnienie, że czytnik blokadę jest nadal ważny, ponieważ środowisko CLR sprawia, że próba podtrzymywania czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="a1f03-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="a1f03-130">Kilka strategii są dostępne dla hosta w celu zapewnienia ważności blokady:</span><span class="sxs-lookup"><span data-stu-id="a1f03-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="a1f03-131">Hosta można zablokować wywołania wersji na blokadę czytnika (na przykład [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) przy jednoczesnym zapewnieniu tego bloku nie powoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a1f03-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="a1f03-132">Host może zablokować opuszczenia oczekiwania na obiekt zdarzenia skojarzonego z czytnika blokadę ponownie zapewnienie tego bloku nie powoduje zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="a1f03-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1f03-133">`CreateRWLockOwnerIterator`musi zostać wywołana tylko dla wątków, które są aktualnie wykonywanych kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a1f03-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f03-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1f03-134">Requirements</span></span>  
 <span data-ttu-id="a1f03-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f03-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f03-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1f03-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1f03-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1f03-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1f03-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f03-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f03-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1f03-139">See Also</span></span>  
 [<span data-ttu-id="a1f03-140">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a1f03-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a1f03-141">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a1f03-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
