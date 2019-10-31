---
title: ICorDebugCode — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 8cb95fad4394e2ce9b7f922e720071d8c4434edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125591"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="7ca98-102">ICorDebugCode — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7ca98-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="7ca98-103">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="7ca98-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ca98-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ca98-104">Methods</span></span>  
  
|<span data-ttu-id="7ca98-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-105">Method</span></span>|<span data-ttu-id="7ca98-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7ca98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ca98-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="7ca98-108">Tworzy punkt przerwania w określonym przesunięciu.</span><span class="sxs-lookup"><span data-stu-id="7ca98-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="7ca98-109">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="7ca98-110">Pobiera względny adres wirtualny (RVA) segmentu kodu, który reprezentuje ten `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7ca98-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="7ca98-111">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="7ca98-112">Pobiera cały kod dla określonej funkcji, sformatowany pod kątem demontażu.</span><span class="sxs-lookup"><span data-stu-id="7ca98-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="7ca98-113">Ta metoda jest przestarzała; Zamiast tego użyj [ICorDebugCode2:: GetCodeChunks —](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ca98-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="7ca98-114">GetEnCRemapSequencePoints, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="7ca98-115">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="7ca98-115">Not implemented.</span></span>|  
|[<span data-ttu-id="7ca98-116">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="7ca98-117">Pobiera wartość "ICorDebugFunction" skojarzoną z tym `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7ca98-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="7ca98-118">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="7ca98-119">Pobiera tablicę wystąpień "COR_DEBUG_IL_TO_NATIVE_MAP", które reprezentują mapowania z przesunięć MSIL do natywnych przesunięć.</span><span class="sxs-lookup"><span data-stu-id="7ca98-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="7ca98-120">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="7ca98-121">Pobiera rozmiar (w bajtach) kodu binarnego reprezentowanego przez ten `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7ca98-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="7ca98-122">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="7ca98-123">Pobiera jednostronicowy numer identyfikujący wersję kodu, który reprezentuje ten `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7ca98-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="7ca98-124">IsIL, metoda</span><span class="sxs-lookup"><span data-stu-id="7ca98-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="7ca98-125">Pobiera wartość wskazującą, czy ten `ICorDebugCode` jest kompilowany w języku MSIL.</span><span class="sxs-lookup"><span data-stu-id="7ca98-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ca98-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ca98-126">Remarks</span></span>  
 <span data-ttu-id="7ca98-127">`ICorDebugCode` może reprezentować kod MSIL lub natywny.</span><span class="sxs-lookup"><span data-stu-id="7ca98-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="7ca98-128">Obiekt "ICorDebugFunction", który reprezentuje kod MSIL, może mieć skojarzone z nim zero lub jeden `ICorDebugCode` obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ca98-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="7ca98-129">Obiekt "ICorDebugFunction" reprezentujący kod natywny może zawierać dowolną liczbę obiektów `ICorDebugCode` skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="7ca98-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ca98-130">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="7ca98-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca98-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ca98-131">Requirements</span></span>  
 <span data-ttu-id="7ca98-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca98-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca98-133">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ca98-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ca98-134">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7ca98-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ca98-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca98-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca98-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ca98-136">See also</span></span>

- [<span data-ttu-id="7ca98-137">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ca98-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="7ca98-138">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7ca98-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
