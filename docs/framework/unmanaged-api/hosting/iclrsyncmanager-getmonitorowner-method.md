---
title: ICLRSyncManager::GetMonitorOwner — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b14421bbe71b68ca677cf712512a7f10aa30583
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763629"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="124f4-102">ICLRSyncManager::GetMonitorOwner — Metoda</span><span class="sxs-lookup"><span data-stu-id="124f4-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="124f4-103">Pobiera [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który jest właścicielem monitor identyfikowane przez określony plik cookie.</span><span class="sxs-lookup"><span data-stu-id="124f4-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="124f4-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="124f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="124f4-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="124f4-106">[in] Plik cookie skojarzone z monitorem.</span><span class="sxs-lookup"><span data-stu-id="124f4-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="124f4-107">[out] Wskaźnik do `IHostTask` , który aktualnie jest właścicielem monitor lub wartość null, jeśli zadanie nie ma prawa własności.</span><span class="sxs-lookup"><span data-stu-id="124f4-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="124f4-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="124f4-108">Return Value</span></span>  
  
|<span data-ttu-id="124f4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="124f4-109">HRESULT</span></span>|<span data-ttu-id="124f4-110">Opis</span><span class="sxs-lookup"><span data-stu-id="124f4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="124f4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="124f4-111">S_OK</span></span>|<span data-ttu-id="124f4-112">`GetMonitorOwner` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="124f4-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="124f4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="124f4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="124f4-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="124f4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="124f4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="124f4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="124f4-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="124f4-116">The call timed out.</span></span>|  
|<span data-ttu-id="124f4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="124f4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="124f4-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="124f4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="124f4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="124f4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="124f4-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="124f4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="124f4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="124f4-121">E_FAIL</span></span>|<span data-ttu-id="124f4-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="124f4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="124f4-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="124f4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="124f4-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="124f4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="124f4-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="124f4-125">Remarks</span></span>  
 <span data-ttu-id="124f4-126">Host zazwyczaj wywołuje `GetMonitorOwner` jako część z mechanizmu wykrywania zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="124f4-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="124f4-127">Plik cookie jest skojarzone z monitorem, gdy jest tworzony przy użyciu wywołania [ihostsyncmanager::createmonitorevent —](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="124f4-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="124f4-128">Wywołanie w celu wydania zdarzeń bazowy monitora może spowodować zablokowanie —, ale nie będzie zakleszczenie — Jeśli wywołanie tej metody jest obecnie obowiązuje w pliku cookie skojarzona z tym monitorem.</span><span class="sxs-lookup"><span data-stu-id="124f4-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="124f4-129">Inne zadania może również zablokować przy próbie uzyskania tego monitora.</span><span class="sxs-lookup"><span data-stu-id="124f4-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="124f4-130">`GetMonitorOwner` zawsze zwraca niezwłocznie i można wywołać w dowolnym momencie po wywołaniu `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="124f4-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="124f4-131">Host nie musi poczekać, aż zadanie trwa oczekiwanie na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="124f4-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="124f4-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="124f4-132">Requirements</span></span>  
 <span data-ttu-id="124f4-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="124f4-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="124f4-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="124f4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="124f4-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="124f4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="124f4-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="124f4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124f4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124f4-137">See also</span></span>

- [<span data-ttu-id="124f4-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="124f4-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="124f4-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="124f4-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
