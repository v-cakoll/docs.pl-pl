---
title: Metoda ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec68e36e2e5a06836d0f5d5758a230591626b03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744105"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="a35dc-102">Metoda ICorDebugVirtualUnwinder::GetContext</span><span class="sxs-lookup"><span data-stu-id="a35dc-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="a35dc-103">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="a35dc-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a35dc-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a35dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a35dc-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="a35dc-106">[in] Flagi określające, które części kontekstu do zwrócenia (zdefiniowanej w pliku WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="a35dc-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="a35dc-107">[in] Liczba bajtów w `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="a35dc-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a35dc-108">[out] Wskaźnik do liczby bajtów rzeczywiście zapisanych na `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="a35dc-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="a35dc-109">[out] Tablica bajtów, która zawiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="a35dc-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a35dc-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a35dc-110">Return Value</span></span>  
 <span data-ttu-id="a35dc-111">Wszelkie kończy się niepowodzeniem, wartość HRESULT odebranych przez mscordbi jest uważane za krytyczne i spowoduje, że icordebug — interfejsy API, aby zwrócić `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="a35dc-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a35dc-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a35dc-112">Remarks</span></span>  
 <span data-ttu-id="a35dc-113">Ustaw wartość początkową `contextBuf` argument do buforu kontekstu zwracany przez wywołanie metody [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a35dc-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a35dc-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a35dc-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="a35dc-115">Ponieważ odwijania maja tylko przywracanie w podzbiorze rejestrów, takich jak trwałej rejestruje tylko, kontekst może nie odpowiadają dokładnie stanu rejestru w momencie wywołania metody rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="a35dc-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35dc-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a35dc-116">Requirements</span></span>  
 <span data-ttu-id="a35dc-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a35dc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35dc-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a35dc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a35dc-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a35dc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a35dc-120">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35dc-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35dc-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a35dc-121">See also</span></span>
- [<span data-ttu-id="a35dc-122">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="a35dc-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a35dc-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a35dc-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
