---
title: "ICorDebugController::HasQueuedCallbacks — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81830cbadcf9fb359b8e1a74cd47f9d18543c29c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="2ca53-102">ICorDebugController::HasQueuedCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ca53-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="2ca53-103">Pobiera wartość wskazującą, czy wszystkie zarządzane wywołania zwrotne aktualnie czekają w kolejce dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="2ca53-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ca53-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ca53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ca53-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="2ca53-106">[in] Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="2ca53-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="2ca53-107">[out] Wskaźnik do wartości, która jest `true` Jeśli wszystkie zarządzane wywołań zwrotnych są obecnie w kolejce dla określonego wątku; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2ca53-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="2ca53-108">Jeśli określono wartość null dla `pThread` parametru `HasQueuedCallbacks` zwróci `true` Jeśli obecnie zarządzane wywołania zwrotne w kolejce na którymkolwiek wątku.</span><span class="sxs-lookup"><span data-stu-id="2ca53-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ca53-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ca53-109">Remarks</span></span>  
 <span data-ttu-id="2ca53-110">Wywołania zwrotne zostaną wysłane pojedynczo, zawsze [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2ca53-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="2ca53-111">Debuger można sprawdzić tej flagi, jeśli chce, aby zgłosić wiele zdarzeń debugowania, które występowały jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="2ca53-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="2ca53-112">Podczas debugowania zdarzenia są umieszczane w kolejce, ich ma już wystąpił, debuger musi opróżniania kolejki całego aby upewnić się, że stan debugowany.</span><span class="sxs-lookup"><span data-stu-id="2ca53-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="2ca53-113">(Wywołania `ICorDebugController::Continue` do opróżnienia kolejki.) Na przykład, jeśli kolejka zawiera dwa zdarzenia debugowania w wątku *X*, i debuger wstrzymuje wątku *X* po pierwsze zdarzenie debugowania, a następnie wywołania `ICorDebugController::Continue`, drugie zdarzenie debugowania dla Wątek *X* zostanie wysłane, mimo że wątek został wstrzymany.</span><span class="sxs-lookup"><span data-stu-id="2ca53-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ca53-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ca53-114">Requirements</span></span>  
 <span data-ttu-id="2ca53-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ca53-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca53-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ca53-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ca53-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ca53-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ca53-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca53-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca53-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ca53-119">See Also</span></span>  
 
