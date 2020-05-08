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
ms.openlocfilehash: bd656445c2451d0583ddbc45e71c9e090bb80305
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892780"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="13913-102">ICorDebugController::HasQueuedCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="13913-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="13913-103">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne są obecnie umieszczane w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="13913-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13913-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13913-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13913-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13913-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="13913-106">podczas Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek.</span><span class="sxs-lookup"><span data-stu-id="13913-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="13913-107">określoną Wskaźnik do wartości, która jest `true` , jeśli jakieś zarządzane wywołania zwrotne są obecnie umieszczane w kolejce dla określonego wątku; w przeciwnym `false`razie.</span><span class="sxs-lookup"><span data-stu-id="13913-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="13913-108">Jeśli wartość null jest określona dla `pThread` parametru, `HasQueuedCallbacks` program zwraca `true` , jeśli w dowolnym wątku istnieją obecnie zarządzane wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="13913-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13913-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13913-109">Remarks</span></span>  
 <span data-ttu-id="13913-110">Wywołania zwrotne będą wysyłane pojedynczo, za każdym razem, gdy [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="13913-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="13913-111">Debuger może zaznaczyć tę flagę, jeśli chce zgłosić wiele zdarzeń debugowania, które wystąpiły jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="13913-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="13913-112">Gdy zdarzenia debugowania są umieszczane w kolejce, są już wystąpiły, więc debuger musi opróżnić całą kolejkę, aby upewnić się, że stan debugowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="13913-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="13913-113">(Wywołanie `ICorDebugController::Continue` do opróżniania kolejki). Na przykład, jeśli kolejka zawiera dwa zdarzenia debugowania w wątku *X*, a debuger wstrzymuje wątek *x* po pierwszym zdarzeniu debugowania, a następnie wywołuje `ICorDebugController::Continue`, drugie zdarzenie debugowania wątku *x* zostanie wysłane, chociaż wątek został zawieszony.</span><span class="sxs-lookup"><span data-stu-id="13913-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13913-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13913-114">Requirements</span></span>  
 <span data-ttu-id="13913-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13913-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13913-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="13913-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13913-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="13913-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13913-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13913-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13913-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13913-119">See also</span></span>
