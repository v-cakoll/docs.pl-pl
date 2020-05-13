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
ms.openlocfilehash: 896e797acc76e8d8034bd964e488317a62eed97b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378775"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="32a7a-102">ICorDebugStackWalk::SetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="32a7a-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="32a7a-103">Ustawia bieżący kontekst obiektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) na prawidłowy kontekst dla wątku.</span><span class="sxs-lookup"><span data-stu-id="32a7a-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32a7a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32a7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32a7a-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="32a7a-106">podczas Flaga [CorDebugSetContextFlag —](cordebugsetcontextflag-enumeration.md) , która wskazuje, czy kontekst pochodzi z aktywnej ramki na stosie, czy kontekst uzyskany przez odmieszczenie stosu.</span><span class="sxs-lookup"><span data-stu-id="32a7a-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="32a7a-107">podczas Przydzielony rozmiar `CONTEXT` buforu.</span><span class="sxs-lookup"><span data-stu-id="32a7a-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="32a7a-108">podczas `CONTEXT`Bufor.</span><span class="sxs-lookup"><span data-stu-id="32a7a-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32a7a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32a7a-109">Return Value</span></span>  
 <span data-ttu-id="32a7a-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="32a7a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="32a7a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32a7a-111">HRESULT</span></span>|<span data-ttu-id="32a7a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="32a7a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32a7a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="32a7a-113">S_OK</span></span>|<span data-ttu-id="32a7a-114">`ICorDebugStackWalk`Kontekst obiektu został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="32a7a-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="32a7a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32a7a-115">E_FAIL</span></span>|<span data-ttu-id="32a7a-116">`ICorDebugStackWalk`Nie ustawiono kontekstu obiektu.</span><span class="sxs-lookup"><span data-stu-id="32a7a-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="32a7a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="32a7a-117">E_INVALIDARG</span></span>|<span data-ttu-id="32a7a-118">Kontekst ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="32a7a-118">The context is null.</span></span>|  
|<span data-ttu-id="32a7a-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="32a7a-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="32a7a-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="32a7a-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="32a7a-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="32a7a-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32a7a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32a7a-122">Remarks</span></span>  
 <span data-ttu-id="32a7a-123">Ta metoda nie zmienia bieżącego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="32a7a-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="32a7a-124">Ustawienie bieżącego kontekstu na nieprawidłowy kontekst może spowodować nieprzewidywalne wyniki z analizatora stosu.</span><span class="sxs-lookup"><span data-stu-id="32a7a-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="32a7a-125">Możesz pobrać dokładną kopię bitową tego kontekstu, natychmiast wywołując metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="32a7a-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a7a-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32a7a-126">Requirements</span></span>  
 <span data-ttu-id="32a7a-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a7a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a7a-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32a7a-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32a7a-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32a7a-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32a7a-130">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a7a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a7a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32a7a-131">See also</span></span>

- [<span data-ttu-id="32a7a-132">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="32a7a-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="32a7a-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="32a7a-133">Debugging</span></span>](index.md)
