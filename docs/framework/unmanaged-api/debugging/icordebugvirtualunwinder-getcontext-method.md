---
title: 'ICorDebugVirtualUnwinder:: GetContext — Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ce54bfd01abb8bd4efd5e46eff1ef831a9f0c8fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121897"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="49637-102">ICorDebugVirtualUnwinder:: GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="49637-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="49637-103">Pobiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="49637-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49637-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49637-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49637-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49637-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="49637-106">podczas Flagi określające, które części kontekstu mają być zwracane (zdefiniowane w WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="49637-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="49637-107">podczas Liczba bajtów w `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="49637-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="49637-108">określoną Wskaźnik do liczby bajtów, które faktycznie Zapisano do `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="49637-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="49637-109">określoną Tablica bajtów, która zawiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="49637-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49637-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49637-110">Return Value</span></span>  
 <span data-ttu-id="49637-111">Wszystkie niepowodzenie wartości HRESULT otrzymanej przez mscordbi jest uznawane za krytyczne i spowoduje, że interfejsy API ICorDebug zwracają `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="49637-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49637-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49637-112">Remarks</span></span>  
 <span data-ttu-id="49637-113">Należy ustawić początkową wartość argumentu `contextBuf` w buforze kontekstu zwracanym przez wywołanie metody [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="49637-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49637-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49637-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="49637-115">Ponieważ rozwinięcia może przywrócić tylko podzestaw rejestrów, takich jak tylko rejestry nielotne, kontekst może nie być dokładnie zgodny z stanem rejestru w chwili rzeczywistego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="49637-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49637-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49637-116">Requirements</span></span>  
 <span data-ttu-id="49637-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49637-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49637-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49637-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49637-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49637-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49637-120">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49637-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49637-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49637-121">See also</span></span>

- [<span data-ttu-id="49637-122">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="49637-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="49637-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="49637-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
