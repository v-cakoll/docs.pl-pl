---
title: 'ICorDebugVirtualUnwinder:: GetContext — Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6a8be489ff2a99bb9da393577514b2442d50db8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967952"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="934ac-102">ICorDebugVirtualUnwinder:: GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="934ac-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="934ac-103">Pobiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="934ac-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="934ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="934ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="934ac-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="934ac-106">podczas Flagi określające, które części kontekstu mają być zwracane (zdefiniowane w WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="934ac-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="934ac-107">podczas Liczba bajtów w `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="934ac-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="934ac-108">określoną Wskaźnik do liczby bajtów, które `contextBuf`są w rzeczywistości zapisywane.</span><span class="sxs-lookup"><span data-stu-id="934ac-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="934ac-109">określoną Tablica bajtów, która zawiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="934ac-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="934ac-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="934ac-110">Return Value</span></span>  
 <span data-ttu-id="934ac-111">Wszystkie niepowodzenie wartości HRESULT otrzymanej przez mscordbi jest uznawane za krytyczne i spowoduje zwrócenie `CORDBG_E_DATA_TARGET_ERROR`interfejsów API ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="934ac-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934ac-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="934ac-112">Remarks</span></span>  
 <span data-ttu-id="934ac-113">Ustawiasz początkową wartość `contextBuf` argumentu dla buforu kontekstu zwracanego przez wywołanie metody [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="934ac-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="934ac-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="934ac-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="934ac-115">Ponieważ rozwinięcia może przywrócić tylko podzestaw rejestrów, takich jak tylko rejestry nielotne, kontekst może nie być dokładnie zgodny z stanem rejestru w chwili rzeczywistego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="934ac-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934ac-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="934ac-116">Requirements</span></span>  
 <span data-ttu-id="934ac-117">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934ac-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934ac-118">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="934ac-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="934ac-119">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="934ac-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="934ac-120">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934ac-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934ac-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="934ac-121">See also</span></span>

- [<span data-ttu-id="934ac-122">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="934ac-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="934ac-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="934ac-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
