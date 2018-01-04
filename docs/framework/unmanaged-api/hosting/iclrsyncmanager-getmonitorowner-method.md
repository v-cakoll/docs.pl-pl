---
title: "ICLRSyncManager::GetMonitorOwner — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetMonitorOwner
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b998a26056aec739587b77c1b1b39f0e9392a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="310f2-102">ICLRSyncManager::GetMonitorOwner — Metoda</span><span class="sxs-lookup"><span data-stu-id="310f2-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="310f2-103">Pobiera [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który jest właścicielem monitor identyfikowane przez określony plik cookie.</span><span class="sxs-lookup"><span data-stu-id="310f2-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="310f2-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="310f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="310f2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="310f2-106">[in] Plik cookie skojarzone z monitorem.</span><span class="sxs-lookup"><span data-stu-id="310f2-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="310f2-107">[out] Wskaźnik do `IHostTask` , który obecnie jest właścicielem monitora lub wartość null, jeśli zadanie nie jest właścicielem.</span><span class="sxs-lookup"><span data-stu-id="310f2-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="310f2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="310f2-108">Return Value</span></span>  
  
|<span data-ttu-id="310f2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="310f2-109">HRESULT</span></span>|<span data-ttu-id="310f2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="310f2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="310f2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="310f2-111">S_OK</span></span>|<span data-ttu-id="310f2-112">`GetMonitorOwner`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="310f2-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="310f2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="310f2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="310f2-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="310f2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="310f2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="310f2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="310f2-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="310f2-116">The call timed out.</span></span>|  
|<span data-ttu-id="310f2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="310f2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="310f2-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="310f2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="310f2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="310f2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="310f2-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="310f2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="310f2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="310f2-121">E_FAIL</span></span>|<span data-ttu-id="310f2-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="310f2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="310f2-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="310f2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="310f2-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="310f2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="310f2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="310f2-125">Remarks</span></span>  
 <span data-ttu-id="310f2-126">Zazwyczaj wymaga hosta `GetMonitorOwner` jako część mechanizm wykrywanie zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="310f2-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="310f2-127">Plik cookie jest skojarzony z monitorem, gdy jest tworzony za pomocą wywołania [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="310f2-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="310f2-128">Wywołanie zwolnienia zdarzeń podstawowy monitor może blokować —, ale nie będzie zakleszczenie — Jeśli wywołanie tej metody działa obecnie na plik cookie skojarzone z tym monitorem.</span><span class="sxs-lookup"><span data-stu-id="310f2-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="310f2-129">Inne zadania mogą również zablokować przy próbie uzyskania tego monitora.</span><span class="sxs-lookup"><span data-stu-id="310f2-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="310f2-130">`GetMonitorOwner`zawsze zwraca natychmiast i można wywołać w dowolnym momencie po wywołaniu `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="310f2-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="310f2-131">Host nie musi poczekać, aż zadanie oczekuje na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="310f2-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="310f2-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="310f2-132">Requirements</span></span>  
 <span data-ttu-id="310f2-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="310f2-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="310f2-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="310f2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="310f2-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="310f2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="310f2-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="310f2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310f2-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="310f2-137">See Also</span></span>  
 [<span data-ttu-id="310f2-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="310f2-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="310f2-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="310f2-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
