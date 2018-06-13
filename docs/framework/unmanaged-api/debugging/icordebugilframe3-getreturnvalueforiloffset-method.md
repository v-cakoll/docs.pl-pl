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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315bd78f660e093ecbf65224bd09a9b4f44300b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420937"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="70f31-102">ICorDebugILFrame3::GetReturnValueForILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="70f31-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="70f31-103">Pobiera obiekt hermetyzujący wartość zwracaną przez funkcję "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="70f31-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70f31-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70f31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70f31-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="70f31-106">Przesunięciu IL.</span><span class="sxs-lookup"><span data-stu-id="70f31-106">The IL offset.</span></span> <span data-ttu-id="70f31-107">W sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="70f31-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="70f31-108">Wskaźnik do adres obiektu interfejsu "ICorDebugValue", który zawiera informacje o wartość zwrotna z wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="70f31-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70f31-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70f31-109">Remarks</span></span>  
 <span data-ttu-id="70f31-110">Ta metoda jest używana wraz z [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metodę, aby pobrać wartość zwracaną przez metodę.</span><span class="sxs-lookup"><span data-stu-id="70f31-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="70f31-111">Jest to szczególnie przydatne w przypadku których wartości zwracane są ignorowane, tak jak w poniższych przykładach kodu dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="70f31-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="70f31-112">Pierwsze wywołania przykład <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody, ale ignoruje wartości zwracanej przez metodę.</span><span class="sxs-lookup"><span data-stu-id="70f31-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="70f31-113">Drugim przykładzie przedstawiono bardziej powszechny problem w debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="70f31-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="70f31-114">Ponieważ metoda jest używana jako argument w wywołaniu metody, jego wartości zwracanej jest dostępna tylko wtedy, gdy debuger przechodzi przez wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="70f31-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="70f31-115">W wielu przypadkach zwłaszcza w przypadku wywołaną metodę jest zdefiniowany w zewnętrznej biblioteki, który nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="70f31-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="70f31-116">W przypadku przekazania [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metody jako IL przesunięcie do lokacji wywołania funkcji, zwraca co najmniej jednego macierzystego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="70f31-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="70f31-117">Debuger można następnie ustawić punkty przerwania w macierzystym przesunięcia w funkcji.</span><span class="sxs-lookup"><span data-stu-id="70f31-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="70f31-118">Gdy debuger trafi jednego z punktów przerwania, można następnie przekazać tej samej przesunięciu IL, który został przekazany do tej metody można pobrać wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="70f31-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="70f31-119">Debuger należy następnie wyczyść wszystkie punkty przerwania, które go ustawić.</span><span class="sxs-lookup"><span data-stu-id="70f31-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="70f31-120">[ICorDebugCode3::GetReturnValueLiveOffset — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) i `ICorDebugILFrame3::GetReturnValueForILOffset` metody umożliwiają uzyskanie informacji zwracanej wartości dla typów referencyjnych tylko.</span><span class="sxs-lookup"><span data-stu-id="70f31-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="70f31-121">Pobieranie informacji o wartości zwracanej z typów wartości (oznacza to, wszystkie typy, które pochodzą z <xref:System.ValueType>) nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="70f31-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="70f31-122">Określone przez przesunięcie IL `ILOffset` parametr powinien być w witrynie wywołania funkcji, a obiekt debugowany powinna zostać zatrzymana na punkt przerwania ustawiony przy przesunięciu natywnego zwrócony przez [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) — metoda dla tego samego przesunięciu IL.</span><span class="sxs-lookup"><span data-stu-id="70f31-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="70f31-123">Obiekt debugowany nie został on zatrzymany w poprawnej lokalizacji dla określonego przesunięcia IL, interfejsu API zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70f31-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="70f31-124">Wywołanie funkcji nie zwraca wartości, interfejsu API zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="70f31-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="70f31-125">`ICorDebugILFrame3::GetReturnValueForILOffset` Metoda jest dostępna tylko na podstawie x86 i systemy AMD64.</span><span class="sxs-lookup"><span data-stu-id="70f31-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70f31-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70f31-126">Requirements</span></span>  
 <span data-ttu-id="70f31-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70f31-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f31-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70f31-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70f31-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70f31-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70f31-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f31-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f31-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70f31-131">See Also</span></span>  
 [<span data-ttu-id="70f31-132">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="70f31-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="70f31-133">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="70f31-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
