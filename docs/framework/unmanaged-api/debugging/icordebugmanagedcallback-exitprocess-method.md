---
title: ICorDebugManagedCallback::ExitProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51162bfb6f9763d2ab4ac1f86e0ccdc15b601271
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159877"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="b685b-102">ICorDebugManagedCallback::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="b685b-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="b685b-103">Powiadamia debugera, że proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="b685b-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b685b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b685b-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b685b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b685b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="b685b-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="b685b-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b685b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b685b-107">Remarks</span></span>  
 <span data-ttu-id="b685b-108">Nie można kontynuować z `ExitProcess` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b685b-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="b685b-109">To zdarzenie może wyzwalać asynchronicznie z innymi zdarzeniami podczas procesu wydaje się być zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="b685b-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="b685b-110">Może to wystąpić, jeśli proces zakończy się po zatrzymaniu zwykle ze względu na pewne siły zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="b685b-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="b685b-111">Jeśli środowisko uruchomieniowe języka wspólnego (CLR) wysyła już zarządzane wywołania zwrotnego, to zdarzenie zostanie opóźnione aż do po zwrócił wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b685b-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="b685b-112">`ExitProcess` Zdarzeń to jedyne zdarzenie zakończenia/zwalnianie, która może zostać wywołana podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="b685b-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b685b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b685b-113">Requirements</span></span>  
 <span data-ttu-id="b685b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b685b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b685b-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b685b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b685b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b685b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b685b-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b685b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b685b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b685b-118">See also</span></span>

- [<span data-ttu-id="b685b-119">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b685b-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
