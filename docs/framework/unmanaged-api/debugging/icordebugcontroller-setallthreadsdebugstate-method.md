---
title: ICorDebugController::SetAllThreadsDebugState — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8d14deae1923e2904818fc01ffa3665fdf5ea6c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710576"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="5d02c-102">ICorDebugController::SetAllThreadsDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d02c-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="5d02c-103">Ustawia stan debugowania wszystkie zarządzane wątki w procesie.</span><span class="sxs-lookup"><span data-stu-id="5d02c-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d02c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d02c-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d02c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d02c-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="5d02c-106">[in] Wartość wyliczenia "Cordebugthreadstate —", który określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5d02c-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="5d02c-107">[in] Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek zwolnione z ustawieniem stanu debugowania.</span><span class="sxs-lookup"><span data-stu-id="5d02c-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="5d02c-108">Jeżeli ta wartość jest równa null, jest wykluczany żadnego wątku.</span><span class="sxs-lookup"><span data-stu-id="5d02c-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d02c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d02c-109">Remarks</span></span>  
 <span data-ttu-id="5d02c-110">`SetAllThreadsDebugState` Metoda może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [enumeratethreads — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), więc wątków, które zostały wstrzymane z `SetAllThreadsDebugState` metody będą musieli można wznowić z `SetAllThreadsDebugState` metody.</span><span class="sxs-lookup"><span data-stu-id="5d02c-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d02c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d02c-111">Requirements</span></span>  
 <span data-ttu-id="5d02c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d02c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d02c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d02c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d02c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d02c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d02c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d02c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d02c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d02c-116">See also</span></span>

