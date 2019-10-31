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
ms.openlocfilehash: 3aec11674275769bb5c4b68521a40a72a1d68a22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124681"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="51e69-102">ICLRSyncManager::GetMonitorOwner — Metoda</span><span class="sxs-lookup"><span data-stu-id="51e69-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="51e69-103">Pobiera wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , które jest właścicielem monitora identyfikowanego przez określony plik cookie.</span><span class="sxs-lookup"><span data-stu-id="51e69-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51e69-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51e69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51e69-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="51e69-106">podczas Plik cookie skojarzony z monitorem.</span><span class="sxs-lookup"><span data-stu-id="51e69-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="51e69-107">określoną Wskaźnik do `IHostTask`, który jest aktualnie właścicielem monitora lub ma wartość null, jeśli żadne zadanie nie ma własności.</span><span class="sxs-lookup"><span data-stu-id="51e69-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51e69-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51e69-108">Return Value</span></span>  
  
|<span data-ttu-id="51e69-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51e69-109">HRESULT</span></span>|<span data-ttu-id="51e69-110">Opis</span><span class="sxs-lookup"><span data-stu-id="51e69-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51e69-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="51e69-111">S_OK</span></span>|<span data-ttu-id="51e69-112">`GetMonitorOwner` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="51e69-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="51e69-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51e69-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51e69-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="51e69-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51e69-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51e69-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51e69-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="51e69-116">The call timed out.</span></span>|  
|<span data-ttu-id="51e69-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51e69-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51e69-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="51e69-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51e69-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51e69-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51e69-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="51e69-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51e69-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51e69-121">E_FAIL</span></span>|<span data-ttu-id="51e69-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="51e69-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51e69-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="51e69-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51e69-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="51e69-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51e69-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51e69-125">Remarks</span></span>  
 <span data-ttu-id="51e69-126">Host zazwyczaj wywołuje `GetMonitorOwner` w ramach mechanizmu wykrywania zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="51e69-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="51e69-127">Plik cookie jest skojarzony z monitorem, gdy jest tworzony przy użyciu wywołania do [IHostSyncManager:: CreateMonitorEvent —](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="51e69-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51e69-128">Wywołanie do zwolnienia zdarzenia podstawowego monitora może być blokowane — ale nie będzie zakleszczenie — Jeśli wywołanie tej metody jest obecnie stosowane dla pliku cookie skojarzonego z tym monitorem.</span><span class="sxs-lookup"><span data-stu-id="51e69-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="51e69-129">Inne zadania mogą być również blokowane, jeśli próbują uzyskać ten monitor.</span><span class="sxs-lookup"><span data-stu-id="51e69-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="51e69-130">`GetMonitorOwner` zawsze wraca natychmiast i może być wywoływana w dowolnym momencie po wywołaniu `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="51e69-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="51e69-131">Host nie musi czekać, aż zadanie oczekuje na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="51e69-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e69-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51e69-132">Requirements</span></span>  
 <span data-ttu-id="51e69-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51e69-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51e69-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="51e69-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51e69-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51e69-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51e69-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51e69-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e69-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51e69-137">See also</span></span>

- [<span data-ttu-id="51e69-138">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="51e69-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="51e69-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="51e69-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
