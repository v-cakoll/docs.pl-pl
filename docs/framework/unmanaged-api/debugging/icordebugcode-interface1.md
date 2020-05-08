---
title: ICorDebugCode, interfejs
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
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893470"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="f478c-102">ICorDebugCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="f478c-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="f478c-103">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f478c-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f478c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f478c-104">Methods</span></span>  
  
|<span data-ttu-id="f478c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-105">Method</span></span>|<span data-ttu-id="f478c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f478c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f478c-107">CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="f478c-108">Tworzy punkt przerwania w określonym przesunięciu.</span><span class="sxs-lookup"><span data-stu-id="f478c-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="f478c-109">GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="f478c-110">Pobiera względny adres wirtualny (RVA) segmentu kodu, który `ICorDebugCode` reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="f478c-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="f478c-111">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="f478c-112">Pobiera cały kod dla określonej funkcji, sformatowany pod kątem demontażu.</span><span class="sxs-lookup"><span data-stu-id="f478c-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="f478c-113">Ta metoda jest przestarzała; Zamiast tego użyj [ICorDebugCode2:: GetCodeChunks —](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f478c-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="f478c-114">GetEnCRemapSequencePoints, metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="f478c-115">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="f478c-115">Not implemented.</span></span>|  
|[<span data-ttu-id="f478c-116">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="f478c-117">Pobiera wartość "ICorDebugFunction" skojarzoną z `ICorDebugCode`tym elementem.</span><span class="sxs-lookup"><span data-stu-id="f478c-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="f478c-118">GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="f478c-119">Pobiera tablicę wystąpień "COR_DEBUG_IL_TO_NATIVE_MAP", które reprezentują mapowania z przesunięć MSIL do natywnych przesunięć.</span><span class="sxs-lookup"><span data-stu-id="f478c-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="f478c-120">GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="f478c-121">Pobiera rozmiar (w bajtach) kodu binarnego reprezentowanego przez ten `ICorDebugCode`element.</span><span class="sxs-lookup"><span data-stu-id="f478c-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="f478c-122">GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="f478c-123">Pobiera jednostronicowy numer identyfikujący wersję kodu, który `ICorDebugCode` reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="f478c-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="f478c-124">IsIL, metoda</span><span class="sxs-lookup"><span data-stu-id="f478c-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="f478c-125">Pobiera wartość wskazującą, czy jest ona `ICorDebugCode` kompilowana w MSIL.</span><span class="sxs-lookup"><span data-stu-id="f478c-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f478c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f478c-126">Remarks</span></span>  
 <span data-ttu-id="f478c-127">`ICorDebugCode`może reprezentować kod MSIL lub natywny.</span><span class="sxs-lookup"><span data-stu-id="f478c-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="f478c-128">Obiekt "ICorDebugFunction", który reprezentuje kod MSIL, może mieć skojarzone z nim `ICorDebugCode` zero lub jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="f478c-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="f478c-129">Obiekt "ICorDebugFunction" reprezentujący kod natywny może zawierać dowolną liczbę `ICorDebugCode` obiektów skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="f478c-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f478c-130">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f478c-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f478c-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f478c-131">Requirements</span></span>  
 <span data-ttu-id="f478c-132">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f478c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f478c-133">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f478c-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f478c-134">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f478c-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f478c-135">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f478c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f478c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f478c-136">See also</span></span>

- [<span data-ttu-id="f478c-137">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f478c-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="f478c-138">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f478c-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
