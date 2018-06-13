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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6025a31f26c635ac40dcc2e35e7017be1c81feba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423019"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="97e6a-102">ICorDebugStackWalk::SetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="97e6a-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="97e6a-103">Ustawia [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) bieżący kontekst obiektu do prawidłowego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="97e6a-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97e6a-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97e6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97e6a-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="97e6a-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flagę wskazującą, czy kontekst jest z aktywną ramkę na stosie, czy kontekst uzyskany przez odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="97e6a-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="97e6a-107">[in] Przydzielony rozmiar `CONTEXT` buforu.</span><span class="sxs-lookup"><span data-stu-id="97e6a-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="97e6a-108">[in] `CONTEXT` Buforu.</span><span class="sxs-lookup"><span data-stu-id="97e6a-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97e6a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="97e6a-109">Return Value</span></span>  
 <span data-ttu-id="97e6a-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="97e6a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="97e6a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97e6a-111">HRESULT</span></span>|<span data-ttu-id="97e6a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="97e6a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97e6a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="97e6a-113">S_OK</span></span>|<span data-ttu-id="97e6a-114">`ICorDebugStackWalk` Pomyślnie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="97e6a-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="97e6a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97e6a-115">E_FAIL</span></span>|<span data-ttu-id="97e6a-116">`ICorDebugStackWalk` Nie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="97e6a-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="97e6a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="97e6a-117">E_INVALIDARG</span></span>|<span data-ttu-id="97e6a-118">Kontekst ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="97e6a-118">The context is null.</span></span>|  
|<span data-ttu-id="97e6a-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="97e6a-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="97e6a-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="97e6a-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="97e6a-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="97e6a-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97e6a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97e6a-122">Remarks</span></span>  
 <span data-ttu-id="97e6a-123">Ta metoda nie zmienia kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="97e6a-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="97e6a-124">Ustawienie w bieżącym kontekście Nieprawidłowy kontekst może spowodować nieoczekiwane wyniki z walkera stosu.</span><span class="sxs-lookup"><span data-stu-id="97e6a-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="97e6a-125">Bitowe dokładną kopię tego kontekstu można pobrać natychmiast wywołując [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="97e6a-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e6a-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97e6a-126">Requirements</span></span>  
 <span data-ttu-id="97e6a-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e6a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e6a-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97e6a-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97e6a-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97e6a-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97e6a-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e6a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e6a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97e6a-131">See Also</span></span>  
 [<span data-ttu-id="97e6a-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="97e6a-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="97e6a-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="97e6a-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
