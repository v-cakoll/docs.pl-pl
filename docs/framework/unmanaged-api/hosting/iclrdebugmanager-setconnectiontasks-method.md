---
title: ICLRDebugManager::SetConnectionTasks — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be3bfc69c551179c99b9fb2134c12f3ab1b2dd63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713226"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="4cb5d-102">ICLRDebugManager::SetConnectionTasks — Metoda</span><span class="sxs-lookup"><span data-stu-id="4cb5d-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="4cb5d-103">Kojarzy listę [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpień przy użyciu identyfikatora i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cb5d-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cb5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cb5d-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="4cb5d-106">[in] Identyfikator określonego hosta do nawiązania połączenia, z którą chcesz skojarzyć `ppCLRTask` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="4cb5d-107">[in] Liczba elementów członkowskich `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="4cb5d-108">Ta liczba musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="4cb5d-109">[in] Tablica `ICLRTask` wskaźników do skojarzenia z tym połączeniem identyfikowane przez `id`.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="4cb5d-110">Tablica musi zawierać co najmniej jednego członka.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cb5d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4cb5d-111">Return Value</span></span>  
  
|<span data-ttu-id="4cb5d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4cb5d-112">HRESULT</span></span>|<span data-ttu-id="4cb5d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4cb5d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4cb5d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cb5d-114">S_OK</span></span>|<span data-ttu-id="4cb5d-115">`SetConnectionTasks` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="4cb5d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4cb5d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4cb5d-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4cb5d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4cb5d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4cb5d-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-119">The call timed out.</span></span>|  
|<span data-ttu-id="4cb5d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cb5d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4cb5d-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4cb5d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4cb5d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4cb5d-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4cb5d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4cb5d-124">E_FAIL</span></span>|<span data-ttu-id="4cb5d-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4cb5d-126">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4cb5d-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4cb5d-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4cb5d-128">E_INVALIDARG</span></span>|<span data-ttu-id="4cb5d-129">[Beginconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nie została wywołana przy użyciu tej wartości `id`, lub `dwCount` lub `id` wynosi zero lub jeden z elementów `ppCLRTask` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cb5d-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cb5d-130">Remarks</span></span>  
 <span data-ttu-id="4cb5d-131">[Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, `SetConnectionTasks`, i [endconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4cb5d-132">Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="4cb5d-133">`BeginConnection` nosi nazwę najpierw nawiązać nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="4cb5d-134">`SetConnectionTasks` wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="4cb5d-135">`EndConnection` wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="4cb5d-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb5d-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cb5d-136">Requirements</span></span>  
 <span data-ttu-id="4cb5d-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb5d-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb5d-138">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cb5d-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cb5d-139">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4cb5d-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cb5d-140">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb5d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb5d-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cb5d-141">See also</span></span>
- [<span data-ttu-id="4cb5d-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cb5d-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4cb5d-143">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cb5d-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="4cb5d-144">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="4cb5d-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="4cb5d-145">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="4cb5d-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="4cb5d-146">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cb5d-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
