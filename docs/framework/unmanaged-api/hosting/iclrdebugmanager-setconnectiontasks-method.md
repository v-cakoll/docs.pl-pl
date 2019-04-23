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
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201991"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="00433-102">ICLRDebugManager::SetConnectionTasks — Metoda</span><span class="sxs-lookup"><span data-stu-id="00433-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="00433-103">Kojarzy listę [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpień przy użyciu identyfikatora i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="00433-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00433-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00433-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00433-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00433-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="00433-106">[in] Identyfikator określonego hosta do nawiązania połączenia, z którą chcesz skojarzyć `ppCLRTask` tablicy.</span><span class="sxs-lookup"><span data-stu-id="00433-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="00433-107">[in] Liczba elementów członkowskich `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="00433-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="00433-108">Ta liczba musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="00433-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="00433-109">[in] Tablica `ICLRTask` wskaźników do skojarzenia z tym połączeniem identyfikowane przez `id`.</span><span class="sxs-lookup"><span data-stu-id="00433-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="00433-110">Tablica musi zawierać co najmniej jednego członka.</span><span class="sxs-lookup"><span data-stu-id="00433-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00433-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="00433-111">Return Value</span></span>  
  
|<span data-ttu-id="00433-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00433-112">HRESULT</span></span>|<span data-ttu-id="00433-113">Opis</span><span class="sxs-lookup"><span data-stu-id="00433-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00433-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="00433-114">S_OK</span></span>|<span data-ttu-id="00433-115">`SetConnectionTasks` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="00433-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="00433-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00433-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00433-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="00433-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00433-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00433-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00433-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="00433-119">The call timed out.</span></span>|  
|<span data-ttu-id="00433-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00433-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00433-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="00433-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00433-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00433-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00433-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="00433-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00433-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00433-124">E_FAIL</span></span>|<span data-ttu-id="00433-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="00433-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00433-126">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="00433-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00433-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="00433-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="00433-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00433-128">E_INVALIDARG</span></span>|<span data-ttu-id="00433-129">[Beginconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nie została wywołana przy użyciu tej wartości `id`, lub `dwCount` lub `id` wynosi zero lub jeden z elementów `ppCLRTask` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="00433-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00433-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00433-130">Remarks</span></span>  
 <span data-ttu-id="00433-131">[Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, `SetConnectionTasks`, i [endconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="00433-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00433-132">Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="00433-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="00433-133">`BeginConnection` nosi nazwę najpierw nawiązać nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="00433-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="00433-134">`SetConnectionTasks` wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="00433-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="00433-135">`EndConnection` wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="00433-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00433-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00433-136">Requirements</span></span>  
 <span data-ttu-id="00433-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00433-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00433-138">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00433-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00433-139">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00433-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00433-140">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00433-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00433-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00433-141">See also</span></span>

- [<span data-ttu-id="00433-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="00433-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="00433-143">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="00433-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="00433-144">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="00433-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="00433-145">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="00433-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="00433-146">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="00433-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
