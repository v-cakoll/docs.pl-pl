---
title: "ICLRDebugManager::SetConnectionTasks — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetConnectionTasks
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f7e47acfcfbde8d5d9724c3a37303f1a584adb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="13c66-102">ICLRDebugManager::SetConnectionTasks — Metoda</span><span class="sxs-lookup"><span data-stu-id="13c66-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="13c66-103">Kojarzy listę [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia o identyfikatorze i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="13c66-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13c66-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13c66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13c66-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="13c66-106">[in] Identyfikator hosta specyficzne dla połączenia, z którą chcesz skojarzyć `ppCLRTask` tablicy.</span><span class="sxs-lookup"><span data-stu-id="13c66-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="13c66-107">[in] Liczba członków `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="13c66-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="13c66-108">Ta liczba musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="13c66-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="13c66-109">[in] Tablica `ICLRTask` wskaźniki do skojarzenia z tym połączeniem identyfikowane przez `id`.</span><span class="sxs-lookup"><span data-stu-id="13c66-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="13c66-110">Tablica musi zawierać co najmniej jednego członka.</span><span class="sxs-lookup"><span data-stu-id="13c66-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13c66-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13c66-111">Return Value</span></span>  
  
|<span data-ttu-id="13c66-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13c66-112">HRESULT</span></span>|<span data-ttu-id="13c66-113">Opis</span><span class="sxs-lookup"><span data-stu-id="13c66-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13c66-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="13c66-114">S_OK</span></span>|<span data-ttu-id="13c66-115">`SetConnectionTasks`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="13c66-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="13c66-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13c66-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13c66-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="13c66-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13c66-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13c66-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13c66-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="13c66-119">The call timed out.</span></span>|  
|<span data-ttu-id="13c66-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13c66-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13c66-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="13c66-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13c66-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13c66-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13c66-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="13c66-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13c66-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13c66-124">E_FAIL</span></span>|<span data-ttu-id="13c66-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="13c66-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13c66-126">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="13c66-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13c66-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="13c66-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="13c66-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="13c66-128">E_INVALIDARG</span></span>|<span data-ttu-id="13c66-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nie została wywołana przy użyciu tej wartości `id`, lub `dwCount` lub `id` wynosi zero lub jeden z elementów `ppCLRTask` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="13c66-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13c66-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13c66-130">Remarks</span></span>  
 <span data-ttu-id="13c66-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) oferuje trzy metody `BeginConnection`, `SetConnectionTasks`, i [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="13c66-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13c66-132">Te trzy metody należy wywołać w dowolnej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="13c66-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="13c66-133">`BeginConnection`jest wywołane najpierw w celu nawiązania nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="13c66-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="13c66-134">`SetConnectionTasks`wywoływana jest następnie podaj zestaw zadań związanych z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="13c66-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="13c66-135">`EndConnection`Aby usunąć skojarzenie między listy zadań identyfikator a przyjazna nazwa jest wywoływana ostatnio. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="13c66-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c66-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13c66-136">Requirements</span></span>  
 <span data-ttu-id="13c66-137">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c66-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c66-138">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13c66-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13c66-139">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13c66-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13c66-140">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c66-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c66-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13c66-141">See Also</span></span>  
 [<span data-ttu-id="13c66-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="13c66-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="13c66-143">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="13c66-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="13c66-144">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="13c66-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="13c66-145">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="13c66-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="13c66-146">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="13c66-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
