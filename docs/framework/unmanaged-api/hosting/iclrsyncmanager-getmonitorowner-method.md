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
ms.openlocfilehash: 77debe047f5b379237022f44ef8f9d96718b227d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762503"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="80ee2-102">ICLRSyncManager::GetMonitorOwner — Metoda</span><span class="sxs-lookup"><span data-stu-id="80ee2-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="80ee2-103">Pobiera wystąpienie [IHostTask](ihosttask-interface.md) , które jest właścicielem monitora identyfikowanego przez określony plik cookie.</span><span class="sxs-lookup"><span data-stu-id="80ee2-103">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ee2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80ee2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80ee2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80ee2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="80ee2-106">podczas Plik cookie skojarzony z monitorem.</span><span class="sxs-lookup"><span data-stu-id="80ee2-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="80ee2-107">określoną Wskaźnik do elementu, `IHostTask` który jest aktualnie właścicielem monitora lub ma wartość null, jeśli żadne zadanie nie ma własności.</span><span class="sxs-lookup"><span data-stu-id="80ee2-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80ee2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80ee2-108">Return Value</span></span>  
  
|<span data-ttu-id="80ee2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80ee2-109">HRESULT</span></span>|<span data-ttu-id="80ee2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="80ee2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80ee2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80ee2-111">S_OK</span></span>|<span data-ttu-id="80ee2-112">`GetMonitorOwner`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="80ee2-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="80ee2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80ee2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80ee2-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="80ee2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80ee2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80ee2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80ee2-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="80ee2-116">The call timed out.</span></span>|  
|<span data-ttu-id="80ee2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80ee2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80ee2-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="80ee2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80ee2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80ee2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80ee2-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="80ee2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80ee2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80ee2-121">E_FAIL</span></span>|<span data-ttu-id="80ee2-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="80ee2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80ee2-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="80ee2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80ee2-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="80ee2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80ee2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80ee2-125">Remarks</span></span>  
 <span data-ttu-id="80ee2-126">Host zazwyczaj wywołuje `GetMonitorOwner` jako część mechanizmu wykrywania zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="80ee2-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="80ee2-127">Plik cookie jest skojarzony z monitorem, gdy jest tworzony przy użyciu wywołania do [IHostSyncManager:: CreateMonitorEvent —](ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="80ee2-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80ee2-128">Wywołanie do zwolnienia zdarzenia podstawowego monitora może być blokowane — ale nie będzie zakleszczenie — Jeśli wywołanie tej metody jest obecnie stosowane dla pliku cookie skojarzonego z tym monitorem.</span><span class="sxs-lookup"><span data-stu-id="80ee2-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="80ee2-129">Inne zadania mogą być również blokowane, jeśli próbują uzyskać ten monitor.</span><span class="sxs-lookup"><span data-stu-id="80ee2-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="80ee2-130">`GetMonitorOwner`zawsze zwraca natychmiast i może być wywoływana w dowolnym momencie po wywołaniu `CreateMonitorEvent` .</span><span class="sxs-lookup"><span data-stu-id="80ee2-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="80ee2-131">Host nie musi czekać, aż zadanie oczekuje na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="80ee2-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ee2-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80ee2-132">Requirements</span></span>  
 <span data-ttu-id="80ee2-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80ee2-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ee2-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80ee2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80ee2-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80ee2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80ee2-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ee2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ee2-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80ee2-137">See also</span></span>

- [<span data-ttu-id="80ee2-138">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="80ee2-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="80ee2-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="80ee2-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
