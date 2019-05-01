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
ms.openlocfilehash: cf21e1844ea99b231054f8350ddacb8bb707a94e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969874"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="aa1a4-102">ICLRDebugManager::EndConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa1a4-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="aa1a4-103">Usuwa skojarzenie między listę zadań i identyfikatora oraz przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa1a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa1a4-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa1a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa1a4-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="aa1a4-106">[in] Identyfikator określonego hosta dla połączenia i skojarzone listy typowe zadania dotyczące języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="aa1a4-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa1a4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa1a4-107">Return Value</span></span>  
  
|<span data-ttu-id="aa1a4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa1a4-108">HRESULT</span></span>|<span data-ttu-id="aa1a4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aa1a4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa1a4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa1a4-110">S_OK</span></span>|<span data-ttu-id="aa1a4-111">`EndConnection` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="aa1a4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa1a4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa1a4-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa1a4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa1a4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa1a4-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-115">The call timed out.</span></span>|  
|<span data-ttu-id="aa1a4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa1a4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa1a4-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa1a4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa1a4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa1a4-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa1a4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa1a4-120">E_FAIL</span></span>|<span data-ttu-id="aa1a4-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa1a4-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa1a4-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa1a4-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="aa1a4-124">E_INVALIDARG</span></span>|<span data-ttu-id="aa1a4-125">[Beginconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nigdy nie została wywołana przy użyciu `dwConnectionId`, lub `dwConnectionId` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa1a4-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa1a4-126">Remarks</span></span>  
 <span data-ttu-id="aa1a4-127">[Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, [setconnectiontasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i `EndConnection`, kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa1a4-128">Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="aa1a4-129">`BeginConnection` nosi nazwę najpierw nawiązać nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="aa1a4-130">`SetConnectionTasks` wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="aa1a4-131">`EndConnection` wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="aa1a4-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa1a4-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa1a4-132">Requirements</span></span>  
 <span data-ttu-id="aa1a4-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa1a4-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa1a4-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa1a4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa1a4-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa1a4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa1a4-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa1a4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1a4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa1a4-137">See also</span></span>

- [<span data-ttu-id="aa1a4-138">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa1a4-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="aa1a4-139">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa1a4-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="aa1a4-140">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="aa1a4-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="aa1a4-141">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="aa1a4-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="aa1a4-142">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa1a4-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
