---
title: ICorDebugController::HasQueuedCallbacks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: 51ee8b3631bffe9fd7fef4351e0aa67d1cbbe2c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125398"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="540b4-102">ICorDebugController::HasQueuedCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="540b4-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="540b4-103">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne są obecnie umieszczane w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="540b4-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="540b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="540b4-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="540b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="540b4-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="540b4-106">podczas Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek.</span><span class="sxs-lookup"><span data-stu-id="540b4-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="540b4-107">określoną Wskaźnik do wartości, która jest `true`, jeśli wszystkie zarządzane wywołania zwrotne są obecnie umieszczane w kolejce dla określonego wątku; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="540b4-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="540b4-108">Jeśli określono wartość null dla parametru `pThread`, `HasQueuedCallbacks` zwróci `true`, jeśli w dowolnym wątku istnieją obecnie zarządzane wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="540b4-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="540b4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="540b4-109">Remarks</span></span>  
 <span data-ttu-id="540b4-110">Wywołania zwrotne będą wysyłane pojedynczo, za każdym razem, gdy [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="540b4-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="540b4-111">Debuger może zaznaczyć tę flagę, jeśli chce zgłosić wiele zdarzeń debugowania, które wystąpiły jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="540b4-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="540b4-112">Gdy zdarzenia debugowania są umieszczane w kolejce, są już wystąpiły, więc debuger musi opróżnić całą kolejkę, aby upewnić się, że stan debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="540b4-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="540b4-113">(Wywołaj `ICorDebugController::Continue`, aby opróżnić kolejkę.) Na przykład, jeśli kolejka zawiera dwa zdarzenia debugowania w wątku *x*, a Debuger zawiesza wątek *x* po pierwszym zdarzeniu debugowania, a następnie wywołuje `ICorDebugController::Continue`, drugie zdarzenie debugowania dla wątku *X* zostanie wysłane, mimo że wątek został zawieszony.</span><span class="sxs-lookup"><span data-stu-id="540b4-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="540b4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="540b4-114">Requirements</span></span>  
 <span data-ttu-id="540b4-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="540b4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="540b4-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="540b4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="540b4-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="540b4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="540b4-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="540b4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540b4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="540b4-119">See also</span></span>
