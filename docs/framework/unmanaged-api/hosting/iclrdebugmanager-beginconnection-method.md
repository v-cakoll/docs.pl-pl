---
title: "ICLRDebugManager::BeginConnection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a637ba71dc966cf311526f468393ef4207e10460
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="c9835-102">ICLRDebugManager::BeginConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9835-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="c9835-103">Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć listę zadań z identyfikatorem i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="c9835-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9835-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9835-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9835-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9835-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="c9835-106">[in] Identyfikator do skojarzenia z listy zadań języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c9835-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="c9835-107">[in] Przyjazna nazwa do skojarzenia z listy zadań CLR.</span><span class="sxs-lookup"><span data-stu-id="c9835-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9835-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c9835-108">Return Value</span></span>  
  
|<span data-ttu-id="c9835-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9835-109">HRESULT</span></span>|<span data-ttu-id="c9835-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c9835-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9835-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9835-111">S_OK</span></span>|<span data-ttu-id="c9835-112">`BeginConnection`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c9835-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="c9835-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9835-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9835-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c9835-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9835-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9835-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9835-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c9835-116">The call timed out.</span></span>|  
|<span data-ttu-id="c9835-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9835-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9835-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c9835-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9835-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9835-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9835-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c9835-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9835-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9835-121">E_FAIL</span></span>|<span data-ttu-id="c9835-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c9835-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9835-123">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c9835-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9835-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9835-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9835-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c9835-125">E_INVALIDARG</span></span>|<span data-ttu-id="c9835-126">`dwConnectionId`wynosi zero, lub `BeginConnection` została już wywołana za pomocą tej `dwConnectionId` wartość, lub `szConnectionName` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="c9835-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="c9835-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c9835-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c9835-128">Za mało pamięci może zostać przydzielony do przechowywania listy zadań skojarzonych z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="c9835-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9835-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9835-129">Remarks</span></span>  
 <span data-ttu-id="c9835-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) oferuje trzy metody `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="c9835-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c9835-131">Te trzy metody należy wywołać w dowolnej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="c9835-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="c9835-132">`BeginConnection`jest wywołane najpierw w celu nawiązania nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="c9835-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="c9835-133">`SetConnectionTasks`wywoływana jest następnie podaj zestaw zadań związanych z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="c9835-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="c9835-134">`EndConnection`Aby usunąć skojarzenie między listy zadań identyfikator a przyjazna nazwa jest wywoływana ostatnio. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="c9835-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9835-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9835-135">Requirements</span></span>  
 <span data-ttu-id="c9835-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9835-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9835-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9835-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9835-138">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9835-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9835-139">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9835-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9835-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9835-140">See Also</span></span>  
 [<span data-ttu-id="c9835-141">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9835-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c9835-142">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9835-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="c9835-143">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="c9835-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="c9835-144">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="c9835-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="c9835-145">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9835-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
