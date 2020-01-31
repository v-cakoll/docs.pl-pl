---
title: ICorDebugStackWalk::SetContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 23ad8882ad97e5ceaeb690dfae08a6be55b85f64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791856"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="af88b-102">ICorDebugStackWalk::SetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="af88b-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="af88b-103">Ustawia bieżący kontekst obiektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) na prawidłowy kontekst dla wątku.</span><span class="sxs-lookup"><span data-stu-id="af88b-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af88b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af88b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af88b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af88b-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="af88b-106">podczas Flaga [CorDebugSetContextFlag —](cordebugsetcontextflag-enumeration.md) , która wskazuje, czy kontekst pochodzi z aktywnej ramki na stosie, czy kontekst uzyskany przez odmieszczenie stosu.</span><span class="sxs-lookup"><span data-stu-id="af88b-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="af88b-107">podczas Przydzielony rozmiar buforu `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="af88b-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="af88b-108">podczas Bufor `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="af88b-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af88b-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="af88b-109">Return Value</span></span>  
 <span data-ttu-id="af88b-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="af88b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="af88b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af88b-111">HRESULT</span></span>|<span data-ttu-id="af88b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="af88b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af88b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="af88b-113">S_OK</span></span>|<span data-ttu-id="af88b-114">Kontekst obiektu `ICorDebugStackWalk` został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="af88b-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="af88b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af88b-115">E_FAIL</span></span>|<span data-ttu-id="af88b-116">Nie ustawiono kontekstu obiektu `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="af88b-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="af88b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="af88b-117">E_INVALIDARG</span></span>|<span data-ttu-id="af88b-118">Kontekst ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="af88b-118">The context is null.</span></span>|  
|<span data-ttu-id="af88b-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="af88b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="af88b-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="af88b-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="af88b-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="af88b-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af88b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af88b-122">Remarks</span></span>  
 <span data-ttu-id="af88b-123">Ta metoda nie zmienia bieżącego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="af88b-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="af88b-124">Ustawienie bieżącego kontekstu na nieprawidłowy kontekst może spowodować nieprzewidywalne wyniki z analizatora stosu.</span><span class="sxs-lookup"><span data-stu-id="af88b-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="af88b-125">Możesz pobrać dokładną kopię bitową tego kontekstu, natychmiast wywołując metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af88b-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af88b-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af88b-126">Requirements</span></span>  
 <span data-ttu-id="af88b-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af88b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af88b-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af88b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af88b-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af88b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af88b-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af88b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af88b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af88b-131">See also</span></span>

- [<span data-ttu-id="af88b-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="af88b-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="af88b-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="af88b-133">Debugging</span></span>](index.md)
