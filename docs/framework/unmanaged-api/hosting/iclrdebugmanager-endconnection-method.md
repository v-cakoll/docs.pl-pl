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
ms.openlocfilehash: f524cadf77caec0823411784c68f339207433601
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615794"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="2298a-102">ICLRDebugManager::EndConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="2298a-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="2298a-103">Usuwa skojarzenie między listą zadań i identyfikatorem i przyjazną nazwą.</span><span class="sxs-lookup"><span data-stu-id="2298a-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2298a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2298a-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2298a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2298a-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="2298a-106">podczas Identyfikator specyficzny dla hosta i skojarzona lista zadań środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2298a-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2298a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2298a-107">Return Value</span></span>  
  
|<span data-ttu-id="2298a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2298a-108">HRESULT</span></span>|<span data-ttu-id="2298a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2298a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2298a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2298a-110">S_OK</span></span>|<span data-ttu-id="2298a-111">`EndConnection`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2298a-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="2298a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2298a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2298a-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2298a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2298a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2298a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2298a-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2298a-115">The call timed out.</span></span>|  
|<span data-ttu-id="2298a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2298a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2298a-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2298a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2298a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2298a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2298a-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2298a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2298a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2298a-120">E_FAIL</span></span>|<span data-ttu-id="2298a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2298a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2298a-122">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="2298a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2298a-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2298a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2298a-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2298a-124">E_INVALIDARG</span></span>|<span data-ttu-id="2298a-125">[BeginConnection —](iclrdebugmanager-beginconnection-method.md) nigdy nie został wywołany przy użyciu `dwConnectionId` lub `dwConnectionId` miał wartość zero.</span><span class="sxs-lookup"><span data-stu-id="2298a-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2298a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2298a-126">Remarks</span></span>  
 <span data-ttu-id="2298a-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody, `BeginConnection` , [SetConnectionTasks —](iclrdebugmanager-setconnectiontasks-method.md)i `EndConnection` , do kojarzenia list zadań z identyfikatorami i przyjaznymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="2298a-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2298a-128">Te trzy metody muszą być wywoływane w określonej kolejności dla każdego zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="2298a-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="2298a-129">`BeginConnection`jest wywoływana najpierw w celu nawiązania nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="2298a-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="2298a-130">`SetConnectionTasks`jest wywoływana dalej, aby określić zestaw zadań, które mają być skojarzone z tym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="2298a-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="2298a-131">`EndConnection`jest wywoływana jako Ostatnia, aby usunąć skojarzenie między listą zadań a identyfikatorem i przyjazną nazwą. Jednak wywołania dla różnych połączeń mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="2298a-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2298a-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2298a-132">Requirements</span></span>  
 <span data-ttu-id="2298a-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2298a-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2298a-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2298a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2298a-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2298a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2298a-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2298a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2298a-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2298a-137">See also</span></span>

- [<span data-ttu-id="2298a-138">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2298a-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2298a-139">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2298a-139">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="2298a-140">BeginConnection, metoda</span><span class="sxs-lookup"><span data-stu-id="2298a-140">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="2298a-141">SetConnectionTasks, metoda</span><span class="sxs-lookup"><span data-stu-id="2298a-141">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="2298a-142">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="2298a-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
