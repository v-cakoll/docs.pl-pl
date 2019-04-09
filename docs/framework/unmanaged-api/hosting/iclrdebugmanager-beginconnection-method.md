---
title: ICLRDebugManager::BeginConnection — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b365aaa13b3070662a74ebcfc914f5ed3d291d76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133994"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="91b3b-102">ICLRDebugManager::BeginConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="91b3b-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="91b3b-103">Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć listę zadań z identyfikatorem i przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="91b3b-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91b3b-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91b3b-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="91b3b-106">[in] Identyfikator do skojarzenia z listą typowe zadania dotyczące języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="91b3b-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="91b3b-107">[in] Przyjazną nazwę do skojarzenia z listy zadań CLR.</span><span class="sxs-lookup"><span data-stu-id="91b3b-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91b3b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91b3b-108">Return Value</span></span>  
  
|<span data-ttu-id="91b3b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91b3b-109">HRESULT</span></span>|<span data-ttu-id="91b3b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="91b3b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91b3b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="91b3b-111">S_OK</span></span>|`BeginConnection` <span data-ttu-id="91b3b-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="91b3b-112">returned successfully.</span></span>|  
|<span data-ttu-id="91b3b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91b3b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91b3b-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="91b3b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91b3b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91b3b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91b3b-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="91b3b-116">The call timed out.</span></span>|  
|<span data-ttu-id="91b3b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91b3b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91b3b-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="91b3b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91b3b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91b3b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91b3b-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="91b3b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91b3b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91b3b-121">E_FAIL</span></span>|<span data-ttu-id="91b3b-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="91b3b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91b3b-123">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="91b3b-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91b3b-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91b3b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="91b3b-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="91b3b-125">E_INVALIDARG</span></span>|`dwConnectionId` <span data-ttu-id="91b3b-126">wynosi zero, lub `BeginConnection` została już wywołana za pomocą tego `dwConnectionId` wartość lub `szConnectionName` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="91b3b-126">was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="91b3b-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="91b3b-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="91b3b-128">Za mało pamięci może zostać przydzielone na potrzeby przechowywania na liście zadań skojarzonych z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="91b3b-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91b3b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91b3b-129">Remarks</span></span>  
 <span data-ttu-id="91b3b-130">[Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, [setconnectiontasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i [endconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="91b3b-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91b3b-131">Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="91b3b-131">These three methods must be called in a specific order for each set of tasks.</span></span> `BeginConnection` <span data-ttu-id="91b3b-132">nosi nazwę najpierw nawiązać nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="91b3b-132">is called first to establish a new connection.</span></span> `SetConnectionTasks` <span data-ttu-id="91b3b-133">wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia.</span><span class="sxs-lookup"><span data-stu-id="91b3b-133">is called next to provide the set of tasks to be associated with that connection.</span></span> `EndConnection` <span data-ttu-id="91b3b-134">wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="91b3b-134">is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91b3b-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91b3b-135">Requirements</span></span>  
 <span data-ttu-id="91b3b-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91b3b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91b3b-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="91b3b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91b3b-138">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91b3b-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="91b3b-139">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="91b3b-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91b3b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91b3b-140">See also</span></span>

- [<span data-ttu-id="91b3b-141">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91b3b-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="91b3b-142">ICLRDebugManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91b3b-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="91b3b-143">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="91b3b-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="91b3b-144">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="91b3b-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="91b3b-145">IHostControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91b3b-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
