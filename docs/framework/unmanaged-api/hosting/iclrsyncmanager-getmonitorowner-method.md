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
ms.openlocfilehash: e1c986de068cd79ae3662c82ed24906d42bf2780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759038"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="4c70d-102">ICLRSyncManager::GetMonitorOwner — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c70d-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="4c70d-103">Pobiera [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który jest właścicielem monitor identyfikowane przez określony plik cookie.</span><span class="sxs-lookup"><span data-stu-id="4c70d-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c70d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c70d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c70d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c70d-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="4c70d-106">[in] Plik cookie skojarzone z monitorem.</span><span class="sxs-lookup"><span data-stu-id="4c70d-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="4c70d-107">[out] Wskaźnik do `IHostTask` , który aktualnie jest właścicielem monitor lub wartość null, jeśli zadanie nie ma prawa własności.</span><span class="sxs-lookup"><span data-stu-id="4c70d-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c70d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4c70d-108">Return Value</span></span>  
  
|<span data-ttu-id="4c70d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c70d-109">HRESULT</span></span>|<span data-ttu-id="4c70d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4c70d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c70d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c70d-111">S_OK</span></span>|<span data-ttu-id="4c70d-112">`GetMonitorOwner` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4c70d-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="4c70d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c70d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c70d-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4c70d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c70d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c70d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c70d-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4c70d-116">The call timed out.</span></span>|  
|<span data-ttu-id="4c70d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c70d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c70d-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="4c70d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c70d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c70d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c70d-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4c70d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c70d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c70d-121">E_FAIL</span></span>|<span data-ttu-id="4c70d-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4c70d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c70d-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4c70d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c70d-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c70d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c70d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c70d-125">Remarks</span></span>  
 <span data-ttu-id="4c70d-126">Host zazwyczaj wywołuje `GetMonitorOwner` jako część z mechanizmu wykrywania zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="4c70d-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="4c70d-127">Plik cookie jest skojarzone z monitorem, gdy jest tworzony przy użyciu wywołania [ihostsyncmanager::createmonitorevent —](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c70d-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c70d-128">Wywołanie w celu wydania zdarzeń bazowy monitora może spowodować zablokowanie —, ale nie będzie zakleszczenie — Jeśli wywołanie tej metody jest obecnie obowiązuje w pliku cookie skojarzona z tym monitorem.</span><span class="sxs-lookup"><span data-stu-id="4c70d-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="4c70d-129">Inne zadania może również zablokować przy próbie uzyskania tego monitora.</span><span class="sxs-lookup"><span data-stu-id="4c70d-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="4c70d-130">`GetMonitorOwner` zawsze zwraca niezwłocznie i można wywołać w dowolnym momencie po wywołaniu `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="4c70d-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="4c70d-131">Host nie musi poczekać, aż zadanie trwa oczekiwanie na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4c70d-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c70d-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c70d-132">Requirements</span></span>  
 <span data-ttu-id="4c70d-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c70d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c70d-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c70d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c70d-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c70d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c70d-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c70d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c70d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c70d-137">See also</span></span>

- [<span data-ttu-id="4c70d-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c70d-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4c70d-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c70d-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
