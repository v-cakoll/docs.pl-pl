---
title: ICorDebugStackWalk::GetContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 700e0af05828b9fe0a50c1aac114e840adc276b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131847"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="fae3e-102">ICorDebugStackWalk::GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="fae3e-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="fae3e-103">Zwraca kontekst dla bieżącej ramki w obiekcie [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fae3e-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fae3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fae3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fae3e-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="fae3e-106">podczas Flagi wskazujące żądaną zawartość buforu kontekstu (zdefiniowaną w WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="fae3e-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="fae3e-107">podczas Przydzielony rozmiar buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fae3e-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="fae3e-108">określoną Rzeczywisty rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fae3e-108">[out] The actual size of the context.</span></span> <span data-ttu-id="fae3e-109">Ta wartość musi być mniejsza lub równa rozmiarowi buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fae3e-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="fae3e-110">określoną Bufor kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fae3e-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fae3e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fae3e-111">Return Value</span></span>  
 <span data-ttu-id="fae3e-112">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="fae3e-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fae3e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fae3e-113">HRESULT</span></span>|<span data-ttu-id="fae3e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fae3e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fae3e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fae3e-115">S_OK</span></span>|<span data-ttu-id="fae3e-116">Kontekst dla bieżącej ramki został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="fae3e-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="fae3e-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fae3e-117">E_FAIL</span></span>|<span data-ttu-id="fae3e-118">Nie można zwrócić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fae3e-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="fae3e-119">HRESULT_FROM_WIN32 (BUFOR ERROR_INSUFFICIENT)</span><span class="sxs-lookup"><span data-stu-id="fae3e-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="fae3e-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="fae3e-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="fae3e-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="fae3e-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="fae3e-122">Wskaźnik ramki znajduje się już na końcu stosu; w związku z tym nie można uzyskać dostępu do dodatkowych ramek.</span><span class="sxs-lookup"><span data-stu-id="fae3e-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="fae3e-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="fae3e-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fae3e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fae3e-124">Remarks</span></span>  
 <span data-ttu-id="fae3e-125">Ponieważ rozwinięcia powoduje przywrócenie tylko podzbioru rejestrów, takich jak rejestry nietrwałe, kontekst może nie być dokładnie zgodny z stanem rejestru w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="fae3e-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae3e-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fae3e-126">Requirements</span></span>  
 <span data-ttu-id="fae3e-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fae3e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fae3e-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fae3e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fae3e-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fae3e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fae3e-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fae3e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae3e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fae3e-131">See also</span></span>

- [<span data-ttu-id="fae3e-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fae3e-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fae3e-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fae3e-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
