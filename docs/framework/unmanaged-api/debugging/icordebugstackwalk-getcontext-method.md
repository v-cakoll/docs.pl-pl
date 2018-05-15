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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1126842a30f19831cc845bcfccc0e08f4bf5f6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="d23d2-102">ICorDebugStackWalk::GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="d23d2-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="d23d2-103">Zwraca kontekst dla bieżącej ramki [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d23d2-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d23d2-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d23d2-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="d23d2-106">[in] Flagi, które wskazują żądanej zawartości buforu kontekstu (zdefiniowane w pliku WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="d23d2-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="d23d2-107">[in] Przydzielony rozmiar buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d23d2-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d23d2-108">[out] Rzeczywisty rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d23d2-108">[out] The actual size of the context.</span></span> <span data-ttu-id="d23d2-109">Ta wartość musi być większa niż rozmiar buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d23d2-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="d23d2-110">[out] Bufor kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d23d2-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d23d2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d23d2-111">Return Value</span></span>  
 <span data-ttu-id="d23d2-112">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d23d2-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d23d2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d23d2-113">HRESULT</span></span>|<span data-ttu-id="d23d2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d23d2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d23d2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d23d2-115">S_OK</span></span>|<span data-ttu-id="d23d2-116">Pomyślnie zwrócono kontekst dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="d23d2-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="d23d2-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d23d2-117">E_FAIL</span></span>|<span data-ttu-id="d23d2-118">Nie można zwrócić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d23d2-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="d23d2-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="d23d2-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="d23d2-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="d23d2-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="d23d2-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="d23d2-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="d23d2-122">Wskaźnik ramki już znajduje się na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.</span><span class="sxs-lookup"><span data-stu-id="d23d2-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d23d2-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d23d2-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23d2-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d23d2-124">Remarks</span></span>  
 <span data-ttu-id="d23d2-125">Ponieważ rozwinięcia przywraca tylko podzestaw rejestrów, takich jak rejestrów trwałej kontekstu nie może pasować stanu rejestru w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="d23d2-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23d2-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d23d2-126">Requirements</span></span>  
 <span data-ttu-id="d23d2-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d23d2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23d2-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d23d2-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d23d2-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d23d2-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d23d2-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23d2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23d2-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d23d2-131">See Also</span></span>  
 [<span data-ttu-id="d23d2-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d23d2-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d23d2-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d23d2-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
