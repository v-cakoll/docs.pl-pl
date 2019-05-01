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
ms.openlocfilehash: bba1e6c113fb4caa0db8963e238d3eceba0cc8ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782749"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="92099-102">ICorDebugStackWalk::GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="92099-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="92099-103">Zwraca kontekst dla bieżącej ramki [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="92099-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92099-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92099-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92099-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92099-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="92099-106">[in] Flagi, które wskazują żądanej zawartości buforu kontekstu (zdefiniowane w pliku WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="92099-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="92099-107">[in] Przydzielony rozmiar buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92099-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="92099-108">[out] Rzeczywisty rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92099-108">[out] The actual size of the context.</span></span> <span data-ttu-id="92099-109">Ta wartość musi być mniejsza niż lub równy rozmiarowi buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92099-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="92099-110">[out] Buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92099-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92099-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92099-111">Return Value</span></span>  
 <span data-ttu-id="92099-112">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="92099-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="92099-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92099-113">HRESULT</span></span>|<span data-ttu-id="92099-114">Opis</span><span class="sxs-lookup"><span data-stu-id="92099-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92099-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="92099-115">S_OK</span></span>|<span data-ttu-id="92099-116">Kontekst dla bieżącej ramki została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="92099-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="92099-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92099-117">E_FAIL</span></span>|<span data-ttu-id="92099-118">Nie można zwrócić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92099-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="92099-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="92099-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="92099-120">Buforu kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="92099-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="92099-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="92099-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="92099-122">Wskaźnik ramki jest już na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.</span><span class="sxs-lookup"><span data-stu-id="92099-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="92099-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="92099-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92099-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92099-124">Remarks</span></span>  
 <span data-ttu-id="92099-125">Ponieważ odwijanie przywraca tylko podzbiór rejestrów, takich jak rejestrów trwałej kontekst może nie odpowiadają dokładnie stanu rejestru w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="92099-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92099-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92099-126">Requirements</span></span>  
 <span data-ttu-id="92099-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92099-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92099-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92099-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92099-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92099-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92099-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92099-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92099-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92099-131">See also</span></span>

- [<span data-ttu-id="92099-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="92099-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="92099-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="92099-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
