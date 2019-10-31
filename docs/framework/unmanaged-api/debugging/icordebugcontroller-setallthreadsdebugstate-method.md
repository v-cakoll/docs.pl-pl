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
ms.openlocfilehash: 1190f83e2671216cf1627eeb710ba576e4b2ec93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125358"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="3bfb0-102">ICorDebugController::SetAllThreadsDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="3bfb0-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="3bfb0-103">Ustawia stan debugowania wszystkich zarządzanych wątków w procesie.</span><span class="sxs-lookup"><span data-stu-id="3bfb0-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bfb0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bfb0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bfb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bfb0-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="3bfb0-106">podczas Wartość wyliczenia "CorDebugThreadState —", która określa stan wątku na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="3bfb0-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="3bfb0-107">podczas Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek, który ma zostać wykluczony z ustawienia stanu debugowania.</span><span class="sxs-lookup"><span data-stu-id="3bfb0-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="3bfb0-108">Jeśli ta wartość jest równa null, żaden wątek nie jest wykluczony.</span><span class="sxs-lookup"><span data-stu-id="3bfb0-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bfb0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bfb0-109">Remarks</span></span>  
 <span data-ttu-id="3bfb0-110">Metoda `SetAllThreadsDebugState` może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [metody EnumerateThreads —](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), więc wątki, które zostały zawieszone przy użyciu metody `SetAllThreadsDebugState`, muszą zostać wznowione przy użyciu metody `SetAllThreadsDebugState`.</span><span class="sxs-lookup"><span data-stu-id="3bfb0-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bfb0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bfb0-111">Requirements</span></span>  
 <span data-ttu-id="3bfb0-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bfb0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bfb0-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3bfb0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bfb0-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3bfb0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bfb0-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bfb0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bfb0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bfb0-116">See also</span></span>
