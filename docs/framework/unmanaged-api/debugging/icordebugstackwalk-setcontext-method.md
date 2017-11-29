---
title: "ICorDebugStackWalk::SetContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.SetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374092c500d4263a172219c38cbc1b2f0ce293a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="9d908-102">ICorDebugStackWalk::SetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d908-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="9d908-103">Ustawia [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) bieżący kontekst obiektu do prawidłowego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="9d908-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d908-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d908-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d908-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d908-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="9d908-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flagę wskazującą, czy kontekst jest z aktywną ramkę na stosie, czy kontekst uzyskany przez odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="9d908-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="9d908-107">[in] Przydzielony rozmiar `CONTEXT` buforu.</span><span class="sxs-lookup"><span data-stu-id="9d908-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="9d908-108">[in] `CONTEXT` Buforu.</span><span class="sxs-lookup"><span data-stu-id="9d908-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d908-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d908-109">Return Value</span></span>  
 <span data-ttu-id="9d908-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9d908-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9d908-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d908-111">HRESULT</span></span>|<span data-ttu-id="9d908-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9d908-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d908-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d908-113">S_OK</span></span>|<span data-ttu-id="9d908-114">`ICorDebugStackWalk` Pomyślnie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d908-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="9d908-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d908-115">E_FAIL</span></span>|<span data-ttu-id="9d908-116">`ICorDebugStackWalk` Nie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d908-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="9d908-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9d908-117">E_INVALIDARG</span></span>|<span data-ttu-id="9d908-118">Kontekst ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d908-118">The context is null.</span></span>|  
|<span data-ttu-id="9d908-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="9d908-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="9d908-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="9d908-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9d908-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9d908-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d908-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d908-122">Remarks</span></span>  
 <span data-ttu-id="9d908-123">Ta metoda nie zmienia kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="9d908-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="9d908-124">Ustawienie w bieżącym kontekście Nieprawidłowy kontekst może spowodować nieoczekiwane wyniki z walkera stosu.</span><span class="sxs-lookup"><span data-stu-id="9d908-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="9d908-125">Bitowe dokładną kopię tego kontekstu można pobrać natychmiast wywołując [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9d908-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d908-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d908-126">Requirements</span></span>  
 <span data-ttu-id="9d908-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d908-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d908-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d908-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d908-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d908-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d908-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d908-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d908-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d908-131">See Also</span></span>  
 [<span data-ttu-id="9d908-132">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="9d908-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9d908-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9d908-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
