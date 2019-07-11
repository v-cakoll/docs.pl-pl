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
ms.openlocfilehash: 04b8ac6751024e64cc866fce1cfe72fb42e41200
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760439"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="a0583-102">ICorDebugManagedCallback::ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0583-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="a0583-103">Powiadamia debugera, że proces został zakończony.</span><span class="sxs-lookup"><span data-stu-id="a0583-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0583-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0583-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0583-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0583-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a0583-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="a0583-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0583-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0583-107">Remarks</span></span>  
 <span data-ttu-id="a0583-108">Nie można kontynuować z `ExitProcess` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a0583-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="a0583-109">To zdarzenie może wyzwalać asynchronicznie z innymi zdarzeniami podczas procesu wydaje się być zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="a0583-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="a0583-110">Może to wystąpić, jeśli proces zakończy się po zatrzymaniu zwykle ze względu na pewne siły zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="a0583-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="a0583-111">Jeśli środowisko uruchomieniowe języka wspólnego (CLR) wysyła już zarządzane wywołania zwrotnego, to zdarzenie zostanie opóźnione aż do po zwrócił wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a0583-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="a0583-112">`ExitProcess` Zdarzeń to jedyne zdarzenie zakończenia/zwalnianie, która może zostać wywołana podczas zamykania.</span><span class="sxs-lookup"><span data-stu-id="a0583-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0583-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0583-113">Requirements</span></span>  
 <span data-ttu-id="a0583-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0583-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0583-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0583-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0583-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0583-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0583-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0583-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0583-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0583-118">See also</span></span>

- [<span data-ttu-id="a0583-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0583-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
