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
ms.openlocfilehash: 7306ee61d750ae256c93c049819a23d3d61f7297
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116470"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="13a8d-102">ICorDebugStackWalk::SetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="13a8d-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="13a8d-103">Zestawy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu w bieżącym kontekście do prawidłowego kontekstu dla wątku.</span><span class="sxs-lookup"><span data-stu-id="13a8d-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13a8d-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13a8d-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="13a8d-106">[in] A [cordebugsetcontextflag —](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flagę, która wskazuje, czy kontekst jest z aktywną ramkę stosu lub kontekst uzyskanych przez odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="13a8d-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="13a8d-107">[in] Przydzielony rozmiar `CONTEXT` buforu.</span><span class="sxs-lookup"><span data-stu-id="13a8d-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="13a8d-108">[in] `CONTEXT` Buforu.</span><span class="sxs-lookup"><span data-stu-id="13a8d-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13a8d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13a8d-109">Return Value</span></span>  
 <span data-ttu-id="13a8d-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="13a8d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="13a8d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13a8d-111">HRESULT</span></span>|<span data-ttu-id="13a8d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="13a8d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13a8d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="13a8d-113">S_OK</span></span>|<span data-ttu-id="13a8d-114">`ICorDebugStackWalk` Pomyślnie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="13a8d-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="13a8d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13a8d-115">E_FAIL</span></span>|<span data-ttu-id="13a8d-116">`ICorDebugStackWalk` Nie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="13a8d-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="13a8d-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="13a8d-117">E_INVALIDARG</span></span>|<span data-ttu-id="13a8d-118">Kontekst ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="13a8d-118">The context is null.</span></span>|  
|<span data-ttu-id="13a8d-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="13a8d-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="13a8d-120">Buforu kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="13a8d-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="13a8d-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="13a8d-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a8d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13a8d-122">Remarks</span></span>  
 <span data-ttu-id="13a8d-123">Ta metoda nie zmienia bieżący kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="13a8d-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="13a8d-124">Ustawienie bieżącego kontekstu Nieprawidłowy kontekst może spowodować nieprzewidywalne skutki z walker stosu.</span><span class="sxs-lookup"><span data-stu-id="13a8d-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="13a8d-125">Bitowe dokładną kopię tego kontekstu można pobrać natychmiast wywołując [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="13a8d-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a8d-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13a8d-126">Requirements</span></span>  
 <span data-ttu-id="13a8d-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a8d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a8d-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13a8d-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13a8d-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13a8d-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="13a8d-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="13a8d-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13a8d-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13a8d-131">See also</span></span>

- [<span data-ttu-id="13a8d-132">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="13a8d-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="13a8d-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="13a8d-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
