---
title: "ICLRDebugManager::EndConnection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.EndConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 114f2217d22fc270b03d271db4acc44f0edbcca8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="efc8d-102">ICLRDebugManager::EndConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="efc8d-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="efc8d-103">Usuwa skojarzenie listę zadań przyjazną nazwę i identyfikator.</span><span class="sxs-lookup"><span data-stu-id="efc8d-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efc8d-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efc8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efc8d-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="efc8d-106">[in] Identyfikator specyficzne dla hosta dla połączenia i skojarzone listę typowych zadań dotyczących języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="efc8d-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efc8d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="efc8d-107">Return Value</span></span>  
  
|<span data-ttu-id="efc8d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="efc8d-108">HRESULT</span></span>|<span data-ttu-id="efc8d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="efc8d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efc8d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="efc8d-110">S_OK</span></span>|<span data-ttu-id="efc8d-111">`EndConnection`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="efc8d-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="efc8d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efc8d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="efc8d-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="efc8d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="efc8d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="efc8d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="efc8d-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="efc8d-115">The call timed out.</span></span>|  
|<span data-ttu-id="efc8d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="efc8d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="efc8d-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="efc8d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="efc8d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="efc8d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="efc8d-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="efc8d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="efc8d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="efc8d-120">E_FAIL</span></span>|<span data-ttu-id="efc8d-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="efc8d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="efc8d-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="efc8d-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="efc8d-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="efc8d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="efc8d-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="efc8d-124">E_INVALIDARG</span></span>|<span data-ttu-id="efc8d-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nigdy nie została wywołana przy użyciu `dwConnectionId`, lub `dwConnectionId` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="efc8d-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efc8d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efc8d-126">Remarks</span></span>  
 <span data-ttu-id="efc8d-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) oferuje trzy metody `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i `EndConnection`, kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="efc8d-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="efc8d-128">Te trzy metody należy wywołać w dowolnej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="efc8d-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="efc8d-129">`BeginConnection`jest wywołane najpierw w celu nawiązania nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="efc8d-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="efc8d-130">`SetConnectionTasks`wywoływana jest następnie podaj zestaw zadań związanych z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="efc8d-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="efc8d-131">`EndConnection`Aby usunąć skojarzenie między listy zadań identyfikator a przyjazna nazwa jest wywoływana ostatnio. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="efc8d-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc8d-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efc8d-132">Requirements</span></span>  
 <span data-ttu-id="efc8d-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc8d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc8d-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="efc8d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efc8d-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="efc8d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efc8d-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc8d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc8d-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efc8d-137">See Also</span></span>  
 [<span data-ttu-id="efc8d-138">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="efc8d-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="efc8d-139">ICLRDebugManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="efc8d-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="efc8d-140">BeginConnection — metoda</span><span class="sxs-lookup"><span data-stu-id="efc8d-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="efc8d-141">SetConnectionTasks — metoda</span><span class="sxs-lookup"><span data-stu-id="efc8d-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="efc8d-142">IHostControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="efc8d-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
