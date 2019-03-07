---
title: ICLRDebugManager::EndConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60e110e019619f9336b240fdc5aee8fa66c5bcdb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479193"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="fd9e5-102">ICLRDebugManager::EndConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd9e5-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="fd9e5-103">Usuwa skojarzenie między listę zadań i identyfikatora oraz przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd9e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd9e5-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd9e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd9e5-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="fd9e5-106">[in] Identyfikator określonego hosta dla połączenia i skojarzone listy typowe zadania dotyczące języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="fd9e5-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd9e5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fd9e5-107">Return Value</span></span>  
  
|<span data-ttu-id="fd9e5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd9e5-108">HRESULT</span></span>|<span data-ttu-id="fd9e5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fd9e5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd9e5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd9e5-110">S_OK</span></span>|<span data-ttu-id="fd9e5-111">`EndConnection` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="fd9e5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd9e5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd9e5-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd9e5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd9e5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd9e5-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-115">The call timed out.</span></span>|  
|<span data-ttu-id="fd9e5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd9e5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd9e5-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd9e5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd9e5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd9e5-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd9e5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd9e5-120">E_FAIL</span></span>|<span data-ttu-id="fd9e5-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd9e5-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd9e5-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fd9e5-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fd9e5-124">E_INVALIDARG</span></span>|<span data-ttu-id="fd9e5-125">[Beginconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nigdy nie została wywołana przy użyciu `dwConnectionId`, lub `dwConnectionId` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd9e5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd9e5-126">Remarks</span></span>  
 <span data-ttu-id="fd9e5-127">[Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, [setconnectiontasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i `EndConnection`, kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd9e5-128">Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="fd9e5-129">`BeginConnection` nosi nazwę najpierw nawiązać nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="fd9e5-130">`SetConnectionTasks` wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="fd9e5-131">`EndConnection` wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="fd9e5-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd9e5-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd9e5-132">Requirements</span></span>  
 <span data-ttu-id="fd9e5-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd9e5-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd9e5-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd9e5-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd9e5-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd9e5-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd9e5-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9e5-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9e5-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd9e5-137">See also</span></span>
- [<span data-ttu-id="fd9e5-138">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd9e5-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fd9e5-139">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd9e5-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="fd9e5-140">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="fd9e5-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="fd9e5-141">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="fd9e5-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="fd9e5-142">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd9e5-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
