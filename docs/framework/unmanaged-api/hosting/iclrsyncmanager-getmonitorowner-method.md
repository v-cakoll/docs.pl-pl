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
ms.openlocfilehash: 5668d75c831710b4f077c325b40352a518ee2c96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434307"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="fc6c1-102">ICLRSyncManager::GetMonitorOwner — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc6c1-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="fc6c1-103">Pobiera [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który jest właścicielem monitor identyfikowane przez określony plik cookie.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc6c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc6c1-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc6c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc6c1-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="fc6c1-106">[in] Plik cookie skojarzone z monitorem.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="fc6c1-107">[out] Wskaźnik do `IHostTask` , który obecnie jest właścicielem monitora lub wartość null, jeśli zadanie nie jest właścicielem.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc6c1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc6c1-108">Return Value</span></span>  
  
|<span data-ttu-id="fc6c1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc6c1-109">HRESULT</span></span>|<span data-ttu-id="fc6c1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fc6c1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc6c1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc6c1-111">S_OK</span></span>|<span data-ttu-id="fc6c1-112">`GetMonitorOwner` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="fc6c1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc6c1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc6c1-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc6c1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc6c1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc6c1-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-116">The call timed out.</span></span>|  
|<span data-ttu-id="fc6c1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc6c1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc6c1-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc6c1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc6c1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc6c1-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc6c1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc6c1-121">E_FAIL</span></span>|<span data-ttu-id="fc6c1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc6c1-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc6c1-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc6c1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc6c1-125">Remarks</span></span>  
 <span data-ttu-id="fc6c1-126">Zazwyczaj wymaga hosta `GetMonitorOwner` jako część mechanizm wykrywanie zakleszczeń.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="fc6c1-127">Plik cookie jest skojarzony z monitorem, gdy jest tworzony za pomocą wywołania [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="fc6c1-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc6c1-128">Wywołanie zwolnienia zdarzeń podstawowy monitor może blokować —, ale nie będzie zakleszczenie — Jeśli wywołanie tej metody działa obecnie na plik cookie skojarzone z tym monitorem.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="fc6c1-129">Inne zadania mogą również zablokować przy próbie uzyskania tego monitora.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="fc6c1-130">`GetMonitorOwner` zawsze zwraca natychmiast i można wywołać w dowolnym momencie po wywołaniu `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="fc6c1-131">Host nie musi poczekać, aż zadanie oczekuje na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="fc6c1-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc6c1-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc6c1-132">Requirements</span></span>  
 <span data-ttu-id="fc6c1-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc6c1-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc6c1-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc6c1-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc6c1-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc6c1-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc6c1-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc6c1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc6c1-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc6c1-137">See Also</span></span>  
 [<span data-ttu-id="fc6c1-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc6c1-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="fc6c1-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc6c1-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
