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
ms.openlocfilehash: fc25e250938d7549c7a9693bee937d4756268b93
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615816"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="11e9b-102">ICLRDebugManager::BeginConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="11e9b-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="11e9b-103">Ustanawia nowe połączenie między hostem i debugerem w celu skojarzenia listy zadań z identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="11e9b-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11e9b-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11e9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11e9b-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="11e9b-106">podczas Identyfikator do skojarzenia z listą zadań środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="11e9b-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="11e9b-107">podczas Przyjazna nazwa do skojarzenia z listą zadań CLR.</span><span class="sxs-lookup"><span data-stu-id="11e9b-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11e9b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11e9b-108">Return Value</span></span>  
  
|<span data-ttu-id="11e9b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11e9b-109">HRESULT</span></span>|<span data-ttu-id="11e9b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="11e9b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11e9b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="11e9b-111">S_OK</span></span>|<span data-ttu-id="11e9b-112">`BeginConnection`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="11e9b-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="11e9b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11e9b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11e9b-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="11e9b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11e9b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11e9b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11e9b-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="11e9b-116">The call timed out.</span></span>|  
|<span data-ttu-id="11e9b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11e9b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11e9b-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="11e9b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11e9b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11e9b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11e9b-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="11e9b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11e9b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11e9b-121">E_FAIL</span></span>|<span data-ttu-id="11e9b-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11e9b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11e9b-123">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="11e9b-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11e9b-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11e9b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11e9b-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="11e9b-125">E_INVALIDARG</span></span>|<span data-ttu-id="11e9b-126">`dwConnectionId`zero lub `BeginConnection` zostało już wywołane przy użyciu tej `dwConnectionId` wartości lub `szConnectionName` miało wartość null.</span><span class="sxs-lookup"><span data-stu-id="11e9b-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="11e9b-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="11e9b-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="11e9b-128">Za mało pamięci, aby pomieścić listę zadań skojarzonych z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="11e9b-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11e9b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11e9b-129">Remarks</span></span>  
 <span data-ttu-id="11e9b-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody, `BeginConnection` , [SetConnectionTasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)i [EndConnection —](iclrdebugmanager-endconnection-method.md), do kojarzenia list zadań z identyfikatorami i przyjaznymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="11e9b-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="11e9b-131">Te trzy metody muszą być wywoływane w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="11e9b-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="11e9b-132">`BeginConnection`jest wywoływana najpierw w celu nawiązania nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="11e9b-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="11e9b-133">`SetConnectionTasks`jest wywoływana dalej, aby określić zestaw zadań, które mają być skojarzone z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="11e9b-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="11e9b-134">`EndConnection`jest wywoływana jako Ostatnia, aby usunąć skojarzenie między listą zadań a identyfikatorem i przyjazną nazwą. Jednak wywołania dla różnych połączeń mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="11e9b-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e9b-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11e9b-135">Requirements</span></span>  
 <span data-ttu-id="11e9b-136">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11e9b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e9b-137">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="11e9b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11e9b-138">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11e9b-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11e9b-139">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e9b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e9b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11e9b-140">See also</span></span>

- [<span data-ttu-id="11e9b-141">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="11e9b-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="11e9b-142">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11e9b-142">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="11e9b-143">EndConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="11e9b-143">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="11e9b-144">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="11e9b-144">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="11e9b-145">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="11e9b-145">IHostControl Interface</span></span>](ihostcontrol-interface.md)
