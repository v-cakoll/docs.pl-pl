---
title: ICorDebugVirtualUnwinder::GetContext — metoda
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96410466f17bf6b4e8fff235d434f470cabd9249
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="4fff9-102">ICorDebugVirtualUnwinder::GetContext — metoda</span><span class="sxs-lookup"><span data-stu-id="4fff9-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="4fff9-103">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="4fff9-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fff9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fff9-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fff9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fff9-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="4fff9-106">[in] Flagi określające, które części kontekstu do zwrócenia (zdefiniowanej w pliku WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="4fff9-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="4fff9-107">[in] Liczba bajtów w `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="4fff9-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4fff9-108">[out] Wskaźnik do liczba bajtów zapisywanych faktycznie `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="4fff9-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="4fff9-109">[out] Tablica bajtów zawierającą bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="4fff9-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fff9-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4fff9-110">Return Value</span></span>  
 <span data-ttu-id="4fff9-111">Wszelkie niepowodzenia wartość HRESULT odebranych przez mscordbi jest on traktowany jako krytyczny i spowoduje, że ICorDebug interfejsów API powrócić `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="4fff9-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fff9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fff9-112">Remarks</span></span>  
 <span data-ttu-id="4fff9-113">Ustaw wartość początkową z `contextBuf` argument do buforu kontekstu zwrócony przez wywołanie metody [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4fff9-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fff9-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4fff9-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="4fff9-115">Ponieważ odwijaniem może tylko restore a podzestawu rejestrów, takich jak trwałej rejestruje tylko, kontekst nie może pasować stanu rejestru w momencie wywołania metody rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="4fff9-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fff9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fff9-116">Requirements</span></span>  
 <span data-ttu-id="4fff9-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fff9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fff9-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fff9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fff9-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fff9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fff9-120">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fff9-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fff9-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fff9-121">See Also</span></span>  
 [<span data-ttu-id="4fff9-122">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="4fff9-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="4fff9-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4fff9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
