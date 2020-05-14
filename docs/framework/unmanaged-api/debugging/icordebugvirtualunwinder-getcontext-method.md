---
title: 'ICorDebugVirtualUnwinder:: GetContext — Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: e203db78b40bf4305316046cfcd679f3d10d1876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396436"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="3e48a-102">ICorDebugVirtualUnwinder:: GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="3e48a-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="3e48a-103">Pobiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="3e48a-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e48a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e48a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e48a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e48a-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="3e48a-106">podczas Flagi określające, które części kontekstu mają być zwracane (zdefiniowane w WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="3e48a-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="3e48a-107">podczas Liczba bajtów w `contextBuf` .</span><span class="sxs-lookup"><span data-stu-id="3e48a-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="3e48a-108">określoną Wskaźnik do liczby bajtów, które są w rzeczywistości zapisywane `contextBuf` .</span><span class="sxs-lookup"><span data-stu-id="3e48a-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="3e48a-109">określoną Tablica bajtów, która zawiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="3e48a-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e48a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3e48a-110">Return Value</span></span>  
 <span data-ttu-id="3e48a-111">Wszystkie niepowodzenie wartości HRESULT otrzymanej przez mscordbi jest uznawane za krytyczne i spowoduje zwrócenie interfejsów API ICorDebug `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="3e48a-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e48a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e48a-112">Remarks</span></span>  
 <span data-ttu-id="3e48a-113">Ustawiasz początkową wartość `contextBuf` argumentu dla buforu kontekstu zwracanego przez wywołanie metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3e48a-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e48a-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3e48a-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="3e48a-115">Ponieważ rozwinięcia może przywrócić tylko podzestaw rejestrów, takich jak tylko rejestry nielotne, kontekst może nie być dokładnie zgodny z stanem rejestru w chwili rzeczywistego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="3e48a-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e48a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e48a-116">Requirements</span></span>  
 <span data-ttu-id="3e48a-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e48a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e48a-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3e48a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e48a-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3e48a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e48a-120">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e48a-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e48a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e48a-121">See also</span></span>

- [<span data-ttu-id="3e48a-122">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e48a-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="3e48a-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3e48a-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
