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
ms.openlocfilehash: 51d34e68851bc6a60d25f643f63d112396abdc4e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209074"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="cfad9-102">ICorDebugManagedCallback2::CreateConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfad9-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="cfad9-103">Powiadamia debuger o utworzeniu nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="cfad9-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfad9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfad9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfad9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfad9-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="cfad9-106">podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym utworzono połączenie</span><span class="sxs-lookup"><span data-stu-id="cfad9-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="cfad9-107">podczas Identyfikator nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="cfad9-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="cfad9-108">podczas Wskaźnik do nazwy nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="cfad9-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfad9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfad9-109">Remarks</span></span>  
 <span data-ttu-id="cfad9-110">`CreateConnection`Wywołanie zwrotne zostanie wyzwolone w jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="cfad9-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="cfad9-111">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="cfad9-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="cfad9-112">W takim przypadku środowisko uruchomieniowe generuje i wyśle `CreateConnection` zdarzenie oraz [ICorDebugManagedCallback2:: ChangeConnection —](icordebugmanagedcallback2-changeconnection-method.md) dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="cfad9-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="cfad9-113">Gdy host wywołuje [ICLRDebugManager:: BeginConnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) w [interfejsie API hostingu](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="cfad9-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfad9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfad9-114">Requirements</span></span>  
 <span data-ttu-id="cfad9-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfad9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfad9-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cfad9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfad9-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cfad9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfad9-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfad9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfad9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfad9-119">See also</span></span>

- [<span data-ttu-id="cfad9-120">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cfad9-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="cfad9-121">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cfad9-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
