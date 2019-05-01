---
title: ICorDebugModule, interfejs
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
ms.openlocfilehash: 257011562a9ea687ef70b842c6d47219283e158e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988042"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="5a9d9-102">ICorDebugModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9d9-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="5a9d9-103">Reprezentuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) moduł, który jest plikiem wykonywalnym lub biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="5a9d9-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a9d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5a9d9-104">Methods</span></span>  
  
|<span data-ttu-id="5a9d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-105">Method</span></span>|<span data-ttu-id="5a9d9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5a9d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a9d9-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="5a9d9-108">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-108">Not implemented.</span></span>|  
|[<span data-ttu-id="5a9d9-109">EnableClassLoadCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="5a9d9-110">Określa, czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="5a9d9-111">EnableJITDebugging, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="5a9d9-112">Określa, czy kompilator just-in-time (JIT), zachowuje informacje o debugowaniu dla metod, w tym module.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="5a9d9-113">GetAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="5a9d9-114">Pobiera zawierające zestaw dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="5a9d9-115">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="5a9d9-116">Pobiera adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="5a9d9-117">GetClassFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="5a9d9-118">Pobiera ICorDebugClass z metadanych.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="5a9d9-119">GetEditAndContinueSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="5a9d9-120">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-120">Deprecated.</span></span>|  
|[<span data-ttu-id="5a9d9-121">GetFunctionFromRVA, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="5a9d9-122">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-122">Not implemented.</span></span>|  
|[<span data-ttu-id="5a9d9-123">GetFunctionFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="5a9d9-124">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="5a9d9-125">GetGlobalVariableValue, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="5a9d9-126">Pobiera obiekt wartości dla określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="5a9d9-127">GetMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="5a9d9-128">Pobiera metadane wskaźnik interfejsu, który może służyć do sprawdzenia metadane dla modułu.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="5a9d9-129">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="5a9d9-130">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="5a9d9-131">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="5a9d9-132">Pobiera zawierającego procesu dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="5a9d9-133">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="5a9d9-134">Pobiera rozmiar modułu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="5a9d9-135">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="5a9d9-136">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="5a9d9-137">IsDynamic, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="5a9d9-138">Wskazuje, czy moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="5a9d9-139">IsInMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="5a9d9-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="5a9d9-140">Wskazuje, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a9d9-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a9d9-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a9d9-142">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5a9d9-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a9d9-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a9d9-143">Requirements</span></span>  
 <span data-ttu-id="5a9d9-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a9d9-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a9d9-145">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a9d9-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a9d9-146">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a9d9-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a9d9-147">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a9d9-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a9d9-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a9d9-148">See also</span></span>

- [<span data-ttu-id="5a9d9-149">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a9d9-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="5a9d9-150">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5a9d9-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
