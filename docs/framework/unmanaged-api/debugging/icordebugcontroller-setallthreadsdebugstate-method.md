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
ms.openlocfilehash: be7fce700756d7120e0853446b7b307ec77c2080
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783760"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="7ecb8-102">ICorDebugController::SetAllThreadsDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ecb8-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="7ecb8-103">Ustawia stan debugowania wszystkich zarządzanych wątków w procesie.</span><span class="sxs-lookup"><span data-stu-id="7ecb8-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ecb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ecb8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ecb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ecb8-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="7ecb8-106">podczas Wartość wyliczenia "CorDebugThreadState —", która określa stan wątku na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="7ecb8-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="7ecb8-107">podczas Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek, który ma zostać wykluczony z ustawienia stanu debugowania.</span><span class="sxs-lookup"><span data-stu-id="7ecb8-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="7ecb8-108">Jeśli ta wartość jest równa null, żaden wątek nie jest wykluczony.</span><span class="sxs-lookup"><span data-stu-id="7ecb8-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ecb8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ecb8-109">Remarks</span></span>  
 <span data-ttu-id="7ecb8-110">Metoda `SetAllThreadsDebugState` może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [metody EnumerateThreads —](icordebugcontroller-enumeratethreads-method.md), więc wątki, które zostały zawieszone przy użyciu metody `SetAllThreadsDebugState`, muszą zostać wznowione przy użyciu metody `SetAllThreadsDebugState`.</span><span class="sxs-lookup"><span data-stu-id="7ecb8-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ecb8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ecb8-111">Requirements</span></span>  
 <span data-ttu-id="7ecb8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ecb8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ecb8-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ecb8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ecb8-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7ecb8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ecb8-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ecb8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ecb8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ecb8-116">See also</span></span>
