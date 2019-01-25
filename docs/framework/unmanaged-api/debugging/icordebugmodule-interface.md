---
title: ICorDebugModule, interfejs1
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eca28f16f0430e793ad0b91b01db609f835f0a4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671255"
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="cfb7c-102">ICorDebugModule, interfejs1</span><span class="sxs-lookup"><span data-stu-id="cfb7c-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="cfb7c-103">Reprezentuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) moduł, który jest plikiem wykonywalnym lub biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="cfb7c-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfb7c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cfb7c-104">Methods</span></span>  
  
|<span data-ttu-id="cfb7c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-105">Method</span></span>|<span data-ttu-id="cfb7c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cfb7c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfb7c-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="cfb7c-108">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-108">Not implemented.</span></span>|  
|[<span data-ttu-id="cfb7c-109">EnableClassLoadCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="cfb7c-110">Określa, czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="cfb7c-111">EnableJITDebugging, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="cfb7c-112">Określa, czy kompilator just-in-time (JIT), zachowuje informacje o debugowaniu dla metod, w tym module.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="cfb7c-113">GetAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="cfb7c-114">Pobiera zawierające zestaw dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="cfb7c-115">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="cfb7c-116">Pobiera adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="cfb7c-117">GetClassFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="cfb7c-118">Pobiera ICorDebugClass z metadanych.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="cfb7c-119">GetEditAndContinueSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="cfb7c-120">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-120">Deprecated.</span></span>|  
|[<span data-ttu-id="cfb7c-121">GetFunctionFromRVA, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="cfb7c-122">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-122">Not implemented.</span></span>|  
|[<span data-ttu-id="cfb7c-123">GetFunctionFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="cfb7c-124">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="cfb7c-125">GetGlobalVariableValue, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="cfb7c-126">Pobiera obiekt wartości dla określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="cfb7c-127">GetMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="cfb7c-128">Pobiera metadane wskaźnik interfejsu, który może służyć do sprawdzenia metadane dla modułu.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="cfb7c-129">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="cfb7c-130">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="cfb7c-131">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="cfb7c-132">Pobiera zawierającego procesu dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="cfb7c-133">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="cfb7c-134">Pobiera rozmiar modułu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="cfb7c-135">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="cfb7c-136">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="cfb7c-137">IsDynamic, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="cfb7c-138">Wskazuje, czy moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="cfb7c-139">IsInMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="cfb7c-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="cfb7c-140">Wskazuje, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfb7c-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfb7c-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfb7c-142">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="cfb7c-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb7c-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfb7c-143">Requirements</span></span>  
 <span data-ttu-id="cfb7c-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfb7c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb7c-145">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfb7c-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfb7c-146">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfb7c-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfb7c-147">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb7c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb7c-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfb7c-148">See also</span></span>
- [<span data-ttu-id="cfb7c-149">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfb7c-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="cfb7c-150">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cfb7c-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
