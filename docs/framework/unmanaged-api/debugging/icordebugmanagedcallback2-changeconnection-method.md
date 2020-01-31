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
ms.openlocfilehash: d60644d54373dfb3d1d191900df71d3e5f6547a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788291"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="83bb2-102">ICorDebugManagedCallback2::ChangeConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="83bb2-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="83bb2-103">Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="83bb2-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bb2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83bb2-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83bb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83bb2-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="83bb2-106">podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces zawierający połączenie, które uległo zmianie.</span><span class="sxs-lookup"><span data-stu-id="83bb2-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="83bb2-107">podczas Identyfikator zmienionego połączenia.</span><span class="sxs-lookup"><span data-stu-id="83bb2-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83bb2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83bb2-108">Remarks</span></span>  
 <span data-ttu-id="83bb2-109">Wywołanie zwrotne `ChangeConnection` zostanie wyzwolone w jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="83bb2-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="83bb2-110">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="83bb2-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="83bb2-111">W takim przypadku środowisko uruchomieniowe generuje i wyśle zdarzenie [ICorDebugManagedCallback2::](icordebugmanagedcallback2-createconnection-method.md) CreateProcess oraz zdarzenie `ChangeConnection` dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="83bb2-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="83bb2-112">Dla każdego istniejącego połączenia jest generowane zdarzenie `ChangeConnection` niezależnie od tego, czy zestaw zadań tego połączenia został zmieniony od czasu jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="83bb2-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="83bb2-113">Gdy host wywołuje [ICLRDebugManager:: SetConnectionTasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) w [interfejsie API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="83bb2-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="83bb2-114">Debuger powinien skanować wszystkie wątki w procesie, aby pobrać nowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="83bb2-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83bb2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83bb2-115">Requirements</span></span>  
 <span data-ttu-id="83bb2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83bb2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83bb2-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="83bb2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83bb2-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="83bb2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83bb2-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83bb2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bb2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83bb2-120">See also</span></span>

- [<span data-ttu-id="83bb2-121">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="83bb2-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="83bb2-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="83bb2-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
