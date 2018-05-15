---
title: ICorDebugCode Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37917577c802514fcebc3ea0792cbce9bb8a7345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="bd49e-102">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="bd49e-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="bd49e-103">Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="bd49e-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd49e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd49e-104">Methods</span></span>  
  
|<span data-ttu-id="bd49e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-105">Method</span></span>|<span data-ttu-id="bd49e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bd49e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd49e-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="bd49e-108">Tworzy punkt przerwania, od wskazanego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="bd49e-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="bd49e-109">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="bd49e-110">Pobiera wirtualny adres względny (RVA) segment kodu, który to `ICorDebugCode` reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="bd49e-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="bd49e-111">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="bd49e-112">Pobiera cały kod dla określonej funkcji, sformatowany dezasemblacji.</span><span class="sxs-lookup"><span data-stu-id="bd49e-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="bd49e-113">Ta metoda jest przestarzała; Użyj [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="bd49e-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="bd49e-114">GetEnCRemapSequencePoints, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="bd49e-115">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="bd49e-115">Not implemented.</span></span>|  
|[<span data-ttu-id="bd49e-116">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="bd49e-117">Pobiera skojarzone z tym "ICorDebugFunction" `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="bd49e-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="bd49e-118">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="bd49e-119">Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowania z przesunięcia MSIL do natywnej przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="bd49e-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="bd49e-120">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="bd49e-121">Pobiera rozmiar w bajtach kod binarny reprezentowany przez to `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="bd49e-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="bd49e-122">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="bd49e-123">Pobiera numer jedynki, który identyfikuje wersję kodu tego `ICorDebugCode` reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="bd49e-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="bd49e-124">IsIL, metoda</span><span class="sxs-lookup"><span data-stu-id="bd49e-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="bd49e-125">Pobiera wartość wskazującą, czy to `ICorDebugCode` ma być kompilowana w MSIL.</span><span class="sxs-lookup"><span data-stu-id="bd49e-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd49e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd49e-126">Remarks</span></span>  
 <span data-ttu-id="bd49e-127">`ICorDebugCode` może reprezentować MSIL lub kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="bd49e-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="bd49e-128">Obiekt "ICorDebugFunction", który reprezentuje kod MSIL może mieć wartość zero lub jeden `ICorDebugCode` obiektów skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="bd49e-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="bd49e-129">Obiekt "ICorDebugFunction", który reprezentuje kod natywny może mieć dowolną liczbę `ICorDebugCode` obiektów skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="bd49e-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd49e-130">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="bd49e-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd49e-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd49e-131">Requirements</span></span>  
 <span data-ttu-id="bd49e-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd49e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd49e-133">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd49e-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd49e-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd49e-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd49e-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd49e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd49e-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd49e-136">See Also</span></span>  
    
 [<span data-ttu-id="bd49e-137">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd49e-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="bd49e-138">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bd49e-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
