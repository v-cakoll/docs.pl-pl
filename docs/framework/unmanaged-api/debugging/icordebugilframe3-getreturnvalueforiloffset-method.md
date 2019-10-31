---
title: ICorDebugILFrame3::GetReturnValueForILOffset — Metoda
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: c7419e5c3677b5679a0ca5c234463ae6e205b7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090376"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="2f161-102">ICorDebugILFrame3::GetReturnValueForILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f161-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="2f161-103">Pobiera obiekt "ICorDebugValue", który hermetyzuje zwracaną wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f161-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f161-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f161-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f161-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f161-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="2f161-106">Przesunięcie IL.</span><span class="sxs-lookup"><span data-stu-id="2f161-106">The IL offset.</span></span> <span data-ttu-id="2f161-107">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="2f161-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="2f161-108">Wskaźnik do adresu obiektu interfejsu "ICorDebugValue", który zawiera informacje o zwracanej wartości wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f161-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f161-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f161-109">Remarks</span></span>  
 <span data-ttu-id="2f161-110">Ta metoda jest używana razem z metodą [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) w celu uzyskania wartości zwracanej przez metodę.</span><span class="sxs-lookup"><span data-stu-id="2f161-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="2f161-111">Jest to szczególnie przydatne w przypadku metod, których wartości zwracane są ignorowane, jak w poniższych dwóch przykładach kodu.</span><span class="sxs-lookup"><span data-stu-id="2f161-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="2f161-112">Pierwszy przykład wywołuje metodę <xref:System.Int32.TryParse%2A?displayProperty=nameWithType>, ale ignoruje wartość zwracaną metody.</span><span class="sxs-lookup"><span data-stu-id="2f161-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="2f161-113">Drugi przykład ilustruje znacznie bardziej typowy problem w debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="2f161-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="2f161-114">Ponieważ metoda jest używana jako argument w wywołaniu metody, jego wartość zwracana jest dostępna tylko wtedy, gdy debuger przeprowadzi procedurę przez wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="2f161-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="2f161-115">W wielu przypadkach, szczególnie gdy wywołana metoda jest zdefiniowana w zewnętrznej bibliotece, która nie jest możliwa.</span><span class="sxs-lookup"><span data-stu-id="2f161-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="2f161-116">W przypadku przekazania metody [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) przesunięcie Il do witryny wywołania funkcji zwraca jedno lub więcej przesunięć natywnych.</span><span class="sxs-lookup"><span data-stu-id="2f161-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="2f161-117">Debuger może następnie ustawić punkty przerwania dla tych natywnych przesunięć w funkcji.</span><span class="sxs-lookup"><span data-stu-id="2f161-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="2f161-118">Gdy debuger trafi jeden z punktów przerwania, można następnie przekazać to samo przesunięcie IL przekazane do tej metody w celu uzyskania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="2f161-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="2f161-119">Debuger powinien następnie wyczyścić wszystkie ustawione punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="2f161-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2f161-120">Metody [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) i metody `ICorDebugILFrame3::GetReturnValueForILOffset` umożliwiają uzyskanie informacji o wartości zwracanej tylko dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="2f161-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="2f161-121">Pobieranie informacji o wartości zwracanej z typów wartości (to oznacza, że wszystkie typy pochodne od <xref:System.ValueType>) nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2f161-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="2f161-122">Przesunięcie IL określone przez parametr `ILOffset` powinno znajdować się w witrynie wywołania funkcji, a debugowanego obiektu powinien zostać zatrzymany w punkcie przerwania w odniesieniu natywnym zwróconym przez metodę [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) dla tego samego przesunięcia Il.</span><span class="sxs-lookup"><span data-stu-id="2f161-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="2f161-123">Jeśli debugowanego obiektu nie zostanie zatrzymana w prawidłowej lokalizacji określonego przesunięcia IL, interfejs API nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="2f161-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="2f161-124">Jeśli wywołanie funkcji nie zwraca wartości, interfejs API nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="2f161-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="2f161-125">Metoda `ICorDebugILFrame3::GetReturnValueForILOffset` jest dostępna tylko w systemach opartych na architekturze x86 i AMD64.</span><span class="sxs-lookup"><span data-stu-id="2f161-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f161-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f161-126">Requirements</span></span>  
 <span data-ttu-id="2f161-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f161-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f161-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f161-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f161-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f161-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f161-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f161-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f161-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f161-131">See also</span></span>

- [<span data-ttu-id="2f161-132">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="2f161-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="2f161-133">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f161-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
