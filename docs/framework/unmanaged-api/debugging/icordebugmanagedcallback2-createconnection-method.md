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
ms.openlocfilehash: d7024b8c0682b3351d185e518dd149737beb04bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416361"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="7d0ed-102">ICorDebugManagedCallback2::CreateConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d0ed-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="7d0ed-103">Powiadamia debugera, że utworzono nowe połączenie.</span><span class="sxs-lookup"><span data-stu-id="7d0ed-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d0ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d0ed-104">Syntax</span></span>  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d0ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d0ed-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7d0ed-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym utworzono połączenie</span><span class="sxs-lookup"><span data-stu-id="7d0ed-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="7d0ed-107">[in] Identyfikator nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="7d0ed-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="7d0ed-108">[in] Wskaźnik na nazwę nowego połączenia.</span><span class="sxs-lookup"><span data-stu-id="7d0ed-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d0ed-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d0ed-109">Remarks</span></span>  
 <span data-ttu-id="7d0ed-110">A `CreateConnection` wywołania zwrotnego zostanie wyzwolone w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="7d0ed-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="7d0ed-111">Gdy debuger dołącza do procesu, który zawiera połączenia.</span><span class="sxs-lookup"><span data-stu-id="7d0ed-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="7d0ed-112">W takim przypadku wygenerowania i wysyłania środowiska uruchomieniowego `CreateConnection` zdarzeń i [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) zdarzeń dla każdego połączenia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7d0ed-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
-   <span data-ttu-id="7d0ed-113">Gdy host wywołuje [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) w [hostingu API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="7d0ed-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d0ed-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d0ed-114">Requirements</span></span>  
 <span data-ttu-id="7d0ed-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d0ed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d0ed-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d0ed-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d0ed-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d0ed-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d0ed-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d0ed-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d0ed-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d0ed-119">See Also</span></span>  
 [<span data-ttu-id="7d0ed-120">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d0ed-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="7d0ed-121">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d0ed-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
