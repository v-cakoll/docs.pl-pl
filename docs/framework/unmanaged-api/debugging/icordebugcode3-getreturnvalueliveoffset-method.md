---
title: ICorDebugCode3::GetReturnValueLiveOffset — Metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 77cda2c3d30b5926da219a38b762295818ca54a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121194"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="081d6-102">ICorDebugCode3::GetReturnValueLiveOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="081d6-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="081d6-103">W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.</span><span class="sxs-lookup"><span data-stu-id="081d6-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="081d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="081d6-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="081d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="081d6-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="081d6-106">Przesunięcie IL.</span><span class="sxs-lookup"><span data-stu-id="081d6-106">The IL offset.</span></span> <span data-ttu-id="081d6-107">Musi to być witryna wywołania funkcji lub wywołanie funkcji zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="081d6-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="081d6-108">Liczba bajtów dostępnych do przechowywania `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="081d6-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="081d6-109">Wskaźnik do liczby zwróconych przesunięć.</span><span class="sxs-lookup"><span data-stu-id="081d6-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="081d6-110">Zazwyczaj jego wartość wynosi 1, ale Pojedyncza instrukcja IL może mapować na wiele `CALL` instrukcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="081d6-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="081d6-111">Tablica przesunięć natywnych.</span><span class="sxs-lookup"><span data-stu-id="081d6-111">An array of native offsets.</span></span> <span data-ttu-id="081d6-112">Zwykle `pOffsets` zawiera pojedyncze przesunięcie, chociaż Pojedyncza instrukcja IL może mapować na wiele map do wielu `CALL` instrukcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="081d6-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="081d6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="081d6-113">Remarks</span></span>  
 <span data-ttu-id="081d6-114">Ta metoda jest używana razem z metodą [ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) w celu uzyskania wartości zwracanej przez metodę zwracającą typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="081d6-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="081d6-115">Przekazywanie przesunięcia IL do witryny wywołania funkcji do tej metody zwraca jedno lub więcej natywnych przesunięć.</span><span class="sxs-lookup"><span data-stu-id="081d6-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="081d6-116">Debuger może następnie ustawić punkty przerwania dla tych natywnych przesunięć w funkcji.</span><span class="sxs-lookup"><span data-stu-id="081d6-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="081d6-117">Gdy debuger trafi jeden z punktów przerwania, można następnie przekazać to samo przesunięcie IL przekazane do tej metody do metody [ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) w celu uzyskania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="081d6-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="081d6-118">Debuger powinien następnie wyczyścić wszystkie ustawione punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="081d6-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="081d6-119">Metody `ICorDebugCode3::GetReturnValueLiveOffset` i [ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) umożliwiają uzyskanie informacji o wartości zwracanej tylko dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="081d6-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="081d6-120">Pobieranie informacji o wartości zwracanej z typów wartości (to oznacza, że wszystkie typy pochodne od <xref:System.ValueType>) nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="081d6-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="081d6-121">Funkcja zwraca wartości `HRESULT` pokazane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="081d6-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="081d6-122">wartość `HRESULT`</span><span class="sxs-lookup"><span data-stu-id="081d6-122">`HRESULT` value</span></span>|<span data-ttu-id="081d6-123">Opis</span><span class="sxs-lookup"><span data-stu-id="081d6-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="081d6-124">Prawnego.</span><span class="sxs-lookup"><span data-stu-id="081d6-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="081d6-125">Dana witryna przesunięcia IL nie jest instrukcją wywołania lub funkcja zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="081d6-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="081d6-126">Określone przesunięcie IL jest właściwym wywołaniem, ale zwracany typ nie jest obsługiwany przez pobranie wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="081d6-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="081d6-127">Metoda `ICorDebugCode3::GetReturnValueLiveOffset` jest dostępna tylko w systemach opartych na architekturze x86 i AMD64.</span><span class="sxs-lookup"><span data-stu-id="081d6-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="081d6-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="081d6-128">Requirements</span></span>  
 <span data-ttu-id="081d6-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="081d6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="081d6-130">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="081d6-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="081d6-131">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="081d6-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="081d6-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="081d6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081d6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="081d6-133">See also</span></span>

- [<span data-ttu-id="081d6-134">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="081d6-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="081d6-135">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="081d6-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
