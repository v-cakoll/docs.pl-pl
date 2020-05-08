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
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976593"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="21d7e-102">ICorDebugController::SetAllThreadsDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="21d7e-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="21d7e-103">Ustawia stan debugowania wszystkich zarządzanych wątków w procesie.</span><span class="sxs-lookup"><span data-stu-id="21d7e-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21d7e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21d7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21d7e-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="21d7e-106">podczas Wartość wyliczenia "CorDebugThreadState —", która określa stan wątku na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="21d7e-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="21d7e-107">podczas Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek, który ma zostać wykluczony z ustawienia stanu debugowania.</span><span class="sxs-lookup"><span data-stu-id="21d7e-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="21d7e-108">Jeśli ta wartość jest równa null, żaden wątek nie jest wykluczony.</span><span class="sxs-lookup"><span data-stu-id="21d7e-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21d7e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21d7e-109">Remarks</span></span>  
 <span data-ttu-id="21d7e-110">Metoda może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [metody EnumerateThreads —](icordebugcontroller-enumeratethreads-method.md), więc wątki, `SetAllThreadsDebugState` które zostały zawieszone przy użyciu metody, muszą `SetAllThreadsDebugState` zostać wznowione przy użyciu metody. `SetAllThreadsDebugState`</span><span class="sxs-lookup"><span data-stu-id="21d7e-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21d7e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21d7e-111">Requirements</span></span>  
 <span data-ttu-id="21d7e-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21d7e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21d7e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21d7e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21d7e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="21d7e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21d7e-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21d7e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d7e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21d7e-116">See also</span></span>
