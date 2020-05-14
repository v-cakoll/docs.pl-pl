---
title: ICorDebugUnmanagedCallback::DebugEvent — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: 24c316ea6bab11fb55e8e0fc1dc9832a312dbc6a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397196"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="25b2f-102">ICorDebugUnmanagedCallback::DebugEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="25b2f-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="25b2f-103">Powiadamia debuger, że zdarzenie natywne zostało wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="25b2f-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25b2f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25b2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25b2f-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="25b2f-106">podczas Wskaźnik do zdarzenia natywnego.</span><span class="sxs-lookup"><span data-stu-id="25b2f-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="25b2f-107">[w] `true` , jeśli interakcja z zarządzanym stanem procesu jest niemożliwa po wystąpieniu zdarzenia niezarządzanego, do momentu, gdy debuger wywoła [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); w przeciwnym razie, `false` .</span><span class="sxs-lookup"><span data-stu-id="25b2f-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25b2f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25b2f-108">Remarks</span></span>  
 <span data-ttu-id="25b2f-109">Jeśli debugowany wątek jest wątkiem Win32, nie należy używać żadnych elementów członkowskich interfejsu debugowania Win32.</span><span class="sxs-lookup"><span data-stu-id="25b2f-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="25b2f-110">Można wywołać `ICorDebugController::Continue` tylko na wątku Win32 i tylko w przypadku kontynuowania ostatniego zdarzenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="25b2f-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="25b2f-111">`DebugEvent`Wywołanie zwrotne nie jest zgodne ze standardowymi regułami wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="25b2f-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="25b2f-112">Po wywołaniu `DebugEvent` , proces będzie znajdował się w stanie zatrzymania w trybie nieprzetworzonym systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="25b2f-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="25b2f-113">Proces nie zostanie zsynchronizowany.</span><span class="sxs-lookup"><span data-stu-id="25b2f-113">The process will not be synchronized.</span></span> <span data-ttu-id="25b2f-114">Stan zsynchronizowany zostanie automatycznie wprowadzony, gdy będzie to konieczne w celu spełnienia żądań informacji o zarządzanym kodzie, co może spowodować inne zagnieżdżone `DebugEvent` wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="25b2f-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="25b2f-115">Wywołaj [ICorDebugProcess:: ClearCurrentException —](icordebugprocess-clearcurrentexception-method.md) w procesie, aby zignorować zdarzenie wyjątku przed kontynuowaniem procesu.</span><span class="sxs-lookup"><span data-stu-id="25b2f-115">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="25b2f-116">Wywołanie tej metody powoduje wysłanie DBG_CONTINUE, a nie DBG_EXCEPTION_NOT_HANDLED na żądanie kontynuowania, i automatycznie czyści punkty przerwania poza pasmem oraz wyjątki jednoetapowe.</span><span class="sxs-lookup"><span data-stu-id="25b2f-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="25b2f-117">Zdarzenia poza pasmem mogą znajdować się w dowolnym momencie, nawet gdy debugowana aplikacja zostanie zatrzymana i gdy zaległe zdarzenie w paśmie już istnieje.</span><span class="sxs-lookup"><span data-stu-id="25b2f-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="25b2f-118">W .NET Framework w wersji 2,0 debuger powinien natychmiast kontynuować poprzednie zdarzenie punktu przerwania poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="25b2f-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="25b2f-119">Debuger powinien używać metod [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md) i [ICorDebugProcess2:: ClearUnmanagedBreakpoint —](icordebugprocess2-clearunmanagedbreakpoint-method.md) , aby dodawać i usuwać punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="25b2f-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="25b2f-120">Te metody spowodują automatyczne pomijanie wszystkich punktów przerwania poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="25b2f-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="25b2f-121">W związku z tym tylko punkty przerwania poza pasmem, które są wysyłane, powinny być nieprzetworzonymi punktami przerwań, które znajdują się już w strumieniu instrukcji, takich jak wywołanie `DebugBreak` funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="25b2f-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="25b2f-122">Nie należy próbować używać `ICorDebugProcess::ClearCurrentException` , [ICorDebugProcess:: GetThreadContext —](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext —](icordebugprocess-setthreadcontext-method.md)ani żadnych innych elementów członkowskich [debugowania API](index.md).</span><span class="sxs-lookup"><span data-stu-id="25b2f-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b2f-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25b2f-123">Requirements</span></span>  
 <span data-ttu-id="25b2f-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b2f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b2f-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25b2f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25b2f-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25b2f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25b2f-127">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b2f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b2f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25b2f-128">See also</span></span>

- [<span data-ttu-id="25b2f-129">ICorDebugUnmanagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="25b2f-129">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
