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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501927"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="3f465-102">ICorDebugManagedCallback2::CreateConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f465-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="3f465-103">Powiadamia debuger o utworzeniu nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f465-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f465-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f465-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f465-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="3f465-106">podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym utworzono połączenie</span><span class="sxs-lookup"><span data-stu-id="3f465-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="3f465-107">podczas Identyfikator nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f465-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="3f465-108">podczas Wskaźnik do nazwy nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f465-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f465-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f465-109">Remarks</span></span>  
 <span data-ttu-id="3f465-110">`CreateConnection`Wywołanie zwrotne zostanie wyzwolone w jednej z następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="3f465-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="3f465-111">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f465-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="3f465-112">W takim przypadku środowisko uruchomieniowe generuje i wyśle `CreateConnection` zdarzenie oraz [ICorDebugManagedCallback2:: ChangeConnection —](icordebugmanagedcallback2-changeconnection-method.md) dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="3f465-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="3f465-113">Gdy host wywołuje [ICLRDebugManager:: BeginConnection —](../hosting/iclrdebugmanager-beginconnection-method.md) w [interfejsie API hostingu](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f465-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f465-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f465-114">Requirements</span></span>  
 <span data-ttu-id="3f465-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f465-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f465-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f465-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f465-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3f465-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f465-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f465-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f465-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f465-119">See also</span></span>

- [<span data-ttu-id="3f465-120">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f465-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="3f465-121">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f465-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
