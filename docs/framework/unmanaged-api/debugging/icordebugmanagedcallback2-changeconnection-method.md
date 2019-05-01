---
title: ICorDebugManagedCallback2::ChangeConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4eeecc22db5786f66b3d484b521989e71817d8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995127"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="9bbc4-102">ICorDebugManagedCallback2::ChangeConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="9bbc4-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="9bbc4-103">Powiadamia debuger zmieniono zestaw zadań skojarzonych z określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bbc4-104">Syntax</span></span>  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bbc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bbc4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="9bbc4-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces zawierający połączenia, która się zmieniła.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="9bbc4-107">[in] Identyfikator połączenia, która się zmieniła.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bbc4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bbc4-108">Remarks</span></span>  
 <span data-ttu-id="9bbc4-109">A `ChangeConnection` wywołanie zwrotne, które będą uruchamiane w jednym z następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="9bbc4-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="9bbc4-110">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="9bbc4-111">W takim wypadku środowisko uruchomieniowe wygeneruje i wysyłania [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) zdarzeń i `ChangeConnection` zdarzeń dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="9bbc4-112">A `ChangeConnection` zdarzenie jest generowane dla każdego istniejącego połączenia, niezależnie od tego, czy został zmieniony od chwili utworzenia tego połączenia zestawu zadań.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="9bbc4-113">Gdy host wywołuje [iclrdebugmanager::setconnectiontasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) w [interfejs API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc4-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="9bbc4-114">Debuger powinien skanować wszystkie wątki w procesie, aby wczytać nowych zmian.</span><span class="sxs-lookup"><span data-stu-id="9bbc4-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bbc4-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bbc4-115">Requirements</span></span>  
 <span data-ttu-id="9bbc4-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bbc4-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bbc4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bbc4-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bbc4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bbc4-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bbc4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbc4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bbc4-120">See also</span></span>

- [<span data-ttu-id="9bbc4-121">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9bbc4-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="9bbc4-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9bbc4-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
