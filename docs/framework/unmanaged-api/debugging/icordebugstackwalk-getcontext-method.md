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
ms.openlocfilehash: 306eee3c0ce4689d1d6295aba1ef7584841dcc72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731052"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="9ba06-102">ICorDebugStackWalk::GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ba06-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="9ba06-103">Zwraca kontekst dla bieżącej ramki [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ba06-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ba06-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ba06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ba06-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="9ba06-106">[in] Flagi, które wskazują żądanej zawartości buforu kontekstu (zdefiniowane w pliku WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="9ba06-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="9ba06-107">[in] Przydzielony rozmiar buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9ba06-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="9ba06-108">[out] Rzeczywisty rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9ba06-108">[out] The actual size of the context.</span></span> <span data-ttu-id="9ba06-109">Ta wartość musi być mniejsza niż lub równy rozmiarowi buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9ba06-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="9ba06-110">[out] Buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9ba06-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ba06-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ba06-111">Return Value</span></span>  
 <span data-ttu-id="9ba06-112">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9ba06-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9ba06-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ba06-113">HRESULT</span></span>|<span data-ttu-id="9ba06-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9ba06-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ba06-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ba06-115">S_OK</span></span>|<span data-ttu-id="9ba06-116">Kontekst dla bieżącej ramki została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="9ba06-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="9ba06-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ba06-117">E_FAIL</span></span>|<span data-ttu-id="9ba06-118">Nie można zwrócić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9ba06-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="9ba06-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="9ba06-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="9ba06-120">Buforu kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="9ba06-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="9ba06-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="9ba06-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="9ba06-122">Wskaźnik ramki jest już na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.</span><span class="sxs-lookup"><span data-stu-id="9ba06-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9ba06-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9ba06-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ba06-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ba06-124">Remarks</span></span>  
 <span data-ttu-id="9ba06-125">Ponieważ odwijanie przywraca tylko podzbiór rejestrów, takich jak rejestrów trwałej kontekst może nie odpowiadają dokładnie stanu rejestru w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="9ba06-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba06-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ba06-126">Requirements</span></span>  
 <span data-ttu-id="9ba06-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ba06-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba06-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ba06-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ba06-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ba06-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ba06-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba06-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba06-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ba06-131">See also</span></span>
- [<span data-ttu-id="9ba06-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9ba06-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9ba06-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9ba06-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
