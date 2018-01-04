---
title: "ICorDebugManagedCallback2::ChangeConnection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ChangeConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ba7e84c11f2fc8619b7046e222a742ee3298554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="ba850-102">ICorDebugManagedCallback2::ChangeConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba850-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="ba850-103">Powiadamia debuger zmiana zestawu zadań powiązanych z określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="ba850-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba850-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba850-104">Syntax</span></span>  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba850-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba850-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="ba850-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces zawierający połączenie, które zmienione.</span><span class="sxs-lookup"><span data-stu-id="ba850-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="ba850-107">[in] Identyfikator połączenia, które zmienione.</span><span class="sxs-lookup"><span data-stu-id="ba850-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba850-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba850-108">Remarks</span></span>  
 <span data-ttu-id="ba850-109">A `ChangeConnection` wywołania zwrotnego zostanie wyzwolone w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="ba850-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="ba850-110">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="ba850-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="ba850-111">W takim przypadku wygenerowania i wysyłania środowiska uruchomieniowego [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) zdarzeń i `ChangeConnection` zdarzeń dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="ba850-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="ba850-112">A `ChangeConnection` zdarzenie jest generowane dla każdego istniejącego połączenia, niezależnie od tego, czy to połączenie zestawu zadań został zmieniony od czasu jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ba850-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
-   <span data-ttu-id="ba850-113">Gdy host wywołuje [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) w [hostingu API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba850-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="ba850-114">Debuger powinien skanować wszystkie wątki tego procesu w celu odebrania nowych zmian.</span><span class="sxs-lookup"><span data-stu-id="ba850-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba850-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba850-115">Requirements</span></span>  
 <span data-ttu-id="ba850-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba850-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba850-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba850-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba850-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba850-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba850-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba850-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba850-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba850-120">See Also</span></span>  
 [<span data-ttu-id="ba850-121">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba850-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="ba850-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba850-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
