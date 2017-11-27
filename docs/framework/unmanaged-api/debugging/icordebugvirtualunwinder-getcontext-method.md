---
title: "ICorDebugVirtualUnwinder::GetContext — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45a914005e84d33b39d72fce96679e275b921d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="50804-102">ICorDebugVirtualUnwinder::GetContext — metoda</span><span class="sxs-lookup"><span data-stu-id="50804-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="50804-103">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="50804-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50804-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50804-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50804-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50804-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="50804-106">[in] Flagi określające, które części kontekstu do zwrócenia (zdefiniowanej w pliku WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="50804-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="50804-107">[in] Liczba bajtów w `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="50804-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="50804-108">[out] Wskaźnik do liczba bajtów zapisywanych faktycznie `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="50804-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="50804-109">[out] Tablica bajtów zawierającą bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="50804-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50804-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50804-110">Return Value</span></span>  
 <span data-ttu-id="50804-111">Wszelkie niepowodzenia wartość HRESULT odebranych przez mscordbi jest on traktowany jako krytyczny i spowoduje, że ICorDebug interfejsów API powrócić `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="50804-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50804-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50804-112">Remarks</span></span>  
 <span data-ttu-id="50804-113">Ustaw wartość początkową z `contextBuf` argument do buforu kontekstu zwrócony przez wywołanie metody [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="50804-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50804-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="50804-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="50804-115">Ponieważ odwijaniem może tylko restore a podzestawu rejestrów, takich jak trwałej rejestruje tylko, kontekst nie może pasować stanu rejestru w momencie wywołania metody rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="50804-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50804-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50804-116">Requirements</span></span>  
 <span data-ttu-id="50804-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50804-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50804-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50804-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50804-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50804-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50804-120">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50804-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50804-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50804-121">See Also</span></span>  
 [<span data-ttu-id="50804-122">Interfejs ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="50804-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="50804-123">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="50804-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
