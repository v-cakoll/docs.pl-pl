---
title: ICorDebugManagedCallback2::CreateConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d0fc0c65d6c479ee4bf7bf527ee33615d53084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761167"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="86b14-102">ICorDebugManagedCallback2::CreateConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="86b14-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="86b14-103">Powiadamia debugera, że utworzono nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="86b14-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b14-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86b14-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86b14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86b14-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="86b14-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym utworzono połączenie</span><span class="sxs-lookup"><span data-stu-id="86b14-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="86b14-107">[in] Identyfikator nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="86b14-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="86b14-108">[in] Wskaźnik na nazwę nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="86b14-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86b14-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86b14-109">Remarks</span></span>  
 <span data-ttu-id="86b14-110">A `CreateConnection` wywołanie zwrotne, które będą uruchamiane w jednym z następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="86b14-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="86b14-111">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="86b14-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="86b14-112">W takim wypadku środowisko uruchomieniowe wygeneruje i wysyłania `CreateConnection` zdarzeń i [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) zdarzeń dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="86b14-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="86b14-113">Gdy host wywołuje [iclrdebugmanager::beginconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) w [interfejs API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="86b14-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86b14-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86b14-114">Requirements</span></span>  
 <span data-ttu-id="86b14-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86b14-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b14-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86b14-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86b14-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86b14-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86b14-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86b14-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b14-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86b14-119">See also</span></span>

- [<span data-ttu-id="86b14-120">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="86b14-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="86b14-121">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="86b14-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
