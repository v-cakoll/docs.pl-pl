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
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131811"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="98935-102">ICorDebugStackWalk::SetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="98935-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="98935-103">Ustawia bieżący kontekst obiektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) na prawidłowy kontekst dla wątku.</span><span class="sxs-lookup"><span data-stu-id="98935-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98935-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98935-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98935-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98935-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="98935-106">podczas Flaga [CorDebugSetContextFlag —](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) , która wskazuje, czy kontekst pochodzi z aktywnej ramki na stosie, czy kontekst uzyskany przez odmieszczenie stosu.</span><span class="sxs-lookup"><span data-stu-id="98935-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="98935-107">podczas Przydzielony rozmiar buforu `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="98935-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="98935-108">podczas Bufor `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="98935-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98935-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="98935-109">Return Value</span></span>  
 <span data-ttu-id="98935-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="98935-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="98935-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98935-111">HRESULT</span></span>|<span data-ttu-id="98935-112">Opis</span><span class="sxs-lookup"><span data-stu-id="98935-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98935-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="98935-113">S_OK</span></span>|<span data-ttu-id="98935-114">Kontekst obiektu `ICorDebugStackWalk` został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="98935-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="98935-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98935-115">E_FAIL</span></span>|<span data-ttu-id="98935-116">Nie ustawiono kontekstu obiektu `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="98935-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="98935-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="98935-117">E_INVALIDARG</span></span>|<span data-ttu-id="98935-118">Kontekst ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="98935-118">The context is null.</span></span>|  
|<span data-ttu-id="98935-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="98935-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="98935-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="98935-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="98935-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="98935-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98935-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98935-122">Remarks</span></span>  
 <span data-ttu-id="98935-123">Ta metoda nie zmienia bieżącego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="98935-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="98935-124">Ustawienie bieżącego kontekstu na nieprawidłowy kontekst może spowodować nieprzewidywalne wyniki z analizatora stosu.</span><span class="sxs-lookup"><span data-stu-id="98935-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="98935-125">Możesz pobrać dokładną kopię bitową tego kontekstu, natychmiast wywołując metodę [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98935-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98935-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98935-126">Requirements</span></span>  
 <span data-ttu-id="98935-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98935-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98935-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98935-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98935-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="98935-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98935-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98935-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98935-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98935-131">See also</span></span>

- [<span data-ttu-id="98935-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="98935-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="98935-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="98935-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
