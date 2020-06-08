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
ms.openlocfilehash: 7d209b7c319baff912b3462f8ed5f3f30f127750
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501914"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="a4838-102">ICorDebugManagedCallback2::ChangeConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4838-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="a4838-103">Powiadamia debuger o zmianie zestawu zadań skojarzonych z określonym połączeniem.</span><span class="sxs-lookup"><span data-stu-id="a4838-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4838-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4838-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4838-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4838-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a4838-106">podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces zawierający połączenie, które uległo zmianie.</span><span class="sxs-lookup"><span data-stu-id="a4838-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="a4838-107">podczas Identyfikator zmienionego połączenia.</span><span class="sxs-lookup"><span data-stu-id="a4838-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4838-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4838-108">Remarks</span></span>  
 <span data-ttu-id="a4838-109">`ChangeConnection`Wywołanie zwrotne zostanie wyzwolone w jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="a4838-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="a4838-110">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="a4838-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="a4838-111">W takim przypadku środowisko uruchomieniowe generuje i wyśle zdarzenie [ICorDebugManagedCallback2::](icordebugmanagedcallback2-createconnection-method.md) CreateProcess oraz `ChangeConnection` zdarzenie dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a4838-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="a4838-112">`ChangeConnection`Dla każdego istniejącego połączenia generowane jest zdarzenie, niezależnie od tego, czy zestaw zadań tego połączenia został zmieniony od czasu jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="a4838-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="a4838-113">Gdy host wywołuje [ICLRDebugManager:: SetConnectionTasks —](../hosting/iclrdebugmanager-setconnectiontasks-method.md) w [interfejsie API hostingu](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="a4838-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="a4838-114">Debuger powinien skanować wszystkie wątki w procesie, aby pobrać nowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="a4838-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4838-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4838-115">Requirements</span></span>  
 <span data-ttu-id="a4838-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4838-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4838-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4838-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4838-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a4838-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4838-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4838-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4838-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4838-120">See also</span></span>

- [<span data-ttu-id="a4838-121">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a4838-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a4838-122">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a4838-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
