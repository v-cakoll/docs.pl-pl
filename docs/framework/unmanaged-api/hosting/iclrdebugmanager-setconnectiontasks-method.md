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
ms.openlocfilehash: d6092f16804fae39dd9496e8572edd64e1b7e9bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129382"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="9b825-102">ICLRDebugManager::SetConnectionTasks — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b825-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="9b825-103">Kojarzy listę wystąpień [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) z identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="9b825-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b825-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b825-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b825-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b825-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="9b825-106">podczas Identyfikator specyficzny dla hosta dla połączenia, z którym ma zostać skojarzona tablica `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="9b825-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="9b825-107">podczas Liczba członków `ppCLRTask`.</span><span class="sxs-lookup"><span data-stu-id="9b825-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="9b825-108">Ta wartość musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="9b825-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="9b825-109">podczas Tablica wskaźników `ICLRTask` do skojarzenia z połączeniem identyfikowanym przez `id`.</span><span class="sxs-lookup"><span data-stu-id="9b825-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="9b825-110">Ta tablica musi zawierać co najmniej jeden element członkowski.</span><span class="sxs-lookup"><span data-stu-id="9b825-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b825-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9b825-111">Return Value</span></span>  
  
|<span data-ttu-id="9b825-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b825-112">HRESULT</span></span>|<span data-ttu-id="9b825-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9b825-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b825-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b825-114">S_OK</span></span>|<span data-ttu-id="9b825-115">`SetConnectionTasks` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="9b825-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="9b825-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b825-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b825-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9b825-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b825-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b825-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b825-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9b825-119">The call timed out.</span></span>|  
|<span data-ttu-id="9b825-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b825-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b825-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9b825-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b825-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b825-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b825-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="9b825-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b825-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b825-124">E_FAIL</span></span>|<span data-ttu-id="9b825-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9b825-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b825-126">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9b825-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b825-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9b825-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b825-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9b825-128">E_INVALIDARG</span></span>|<span data-ttu-id="9b825-129">[BeginConnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nie został wywołany przy użyciu tej wartości `id`lub `dwCount` lub `id` jest zerem lub jeden z elementów `ppCLRTask` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="9b825-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b825-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b825-130">Remarks</span></span>  
 <span data-ttu-id="9b825-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody, `BeginConnection`, `SetConnectionTasks`i [EndConnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), do kojarzenia list zadań z identyfikatorami i przyjaznymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="9b825-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9b825-132">Te trzy metody muszą być wywoływane w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="9b825-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="9b825-133">`BeginConnection` jest wywoływana najpierw w celu nawiązania nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="9b825-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="9b825-134">`SetConnectionTasks` jest wywoływana dalej, aby określić zestaw zadań, które mają być skojarzone z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="9b825-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="9b825-135">`EndConnection` jest wywoływana jako Ostatnia, aby usunąć skojarzenie między listą zadań a identyfikatorem i przyjazną nazwą. Jednak wywołania dla różnych połączeń mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="9b825-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b825-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b825-136">Requirements</span></span>  
 <span data-ttu-id="9b825-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b825-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b825-138">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9b825-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b825-139">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b825-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b825-140">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b825-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b825-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b825-141">See also</span></span>

- [<span data-ttu-id="9b825-142">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b825-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9b825-143">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b825-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="9b825-144">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="9b825-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="9b825-145">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="9b825-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="9b825-146">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b825-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
