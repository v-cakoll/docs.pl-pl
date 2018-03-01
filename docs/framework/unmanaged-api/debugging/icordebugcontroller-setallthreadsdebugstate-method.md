---
title: "ICorDebugController::SetAllThreadsDebugState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8c9904c3c86e405660dcafe9963fe05049524b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="b2c6d-102">ICorDebugController::SetAllThreadsDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2c6d-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="b2c6d-103">Ustawia stan debugowania wszystkie wątki zarządzane w procesie.</span><span class="sxs-lookup"><span data-stu-id="b2c6d-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2c6d-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2c6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2c6d-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="b2c6d-106">[in] Wartość wyliczenia "CorDebugThreadState", który określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b2c6d-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="b2c6d-107">[in] Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątku zwolnione z ustawienia stanu debugowania.</span><span class="sxs-lookup"><span data-stu-id="b2c6d-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="b2c6d-108">Jeśli ta wartość jest równa null, jest wykluczany żadnego wątku.</span><span class="sxs-lookup"><span data-stu-id="b2c6d-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2c6d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2c6d-109">Remarks</span></span>  
 <span data-ttu-id="b2c6d-110">`SetAllThreadsDebugState` Metody może mieć wpływ na wątków, które nie są widoczne za pośrednictwem [EnumerateThreads — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), tak wątków, które zostały wstrzymane z `SetAllThreadsDebugState` — metoda musi zostać przywrócone `SetAllThreadsDebugState` metody.</span><span class="sxs-lookup"><span data-stu-id="b2c6d-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c6d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2c6d-111">Requirements</span></span>  
 <span data-ttu-id="b2c6d-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c6d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c6d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2c6d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2c6d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2c6d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c6d-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c6d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c6d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2c6d-116">See Also</span></span>  
 
