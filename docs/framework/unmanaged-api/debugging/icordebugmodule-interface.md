---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="0a9d3-102">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="0a9d3-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="0a9d3-103">Reprezentuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) moduł, który jest plik wykonywalny lub biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="0a9d3-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a9d3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0a9d3-104">Methods</span></span>  
  
|<span data-ttu-id="0a9d3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-105">Method</span></span>|<span data-ttu-id="0a9d3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0a9d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a9d3-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="0a9d3-108">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-108">Not implemented.</span></span>|  
|[<span data-ttu-id="0a9d3-109">EnableClassLoadCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="0a9d3-110">Określa, czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołań zwrotnych są nazywane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="0a9d3-111">EnableJITDebugging, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="0a9d3-112">Określa, czy przy użyciu kompilatora just in time (JIT) zachowuje informacji debugowania dla metod w ramach tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="0a9d3-113">GetAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="0a9d3-114">Pobiera zestaw zawierający dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="0a9d3-115">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="0a9d3-116">Pobiera adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="0a9d3-117">GetClassFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="0a9d3-118">Pobiera ICorDebugClass z metadanych.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="0a9d3-119">GetEditAndContinueSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="0a9d3-120">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-120">Deprecated.</span></span>|  
|[<span data-ttu-id="0a9d3-121">GetFunctionFromRVA, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="0a9d3-122">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-122">Not implemented.</span></span>|  
|[<span data-ttu-id="0a9d3-123">GetFunctionFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="0a9d3-124">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="0a9d3-125">GetGlobalVariableValue, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="0a9d3-126">Pobiera obiekt wartości dla określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="0a9d3-127">GetMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="0a9d3-128">Pobiera metadane wskaźnika interfejsu, który może służyć do sprawdzenia metadane dla modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="0a9d3-129">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="0a9d3-130">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="0a9d3-131">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="0a9d3-132">Pobiera zawierający procesu dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="0a9d3-133">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="0a9d3-134">Pobiera moduł rozmiar w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="0a9d3-135">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="0a9d3-136">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="0a9d3-137">IsDynamic, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="0a9d3-138">Wskazuje, czy moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="0a9d3-139">IsInMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="0a9d3-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="0a9d3-140">Wskazuje, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a9d3-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a9d3-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a9d3-142">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="0a9d3-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a9d3-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a9d3-143">Requirements</span></span>  
 <span data-ttu-id="0a9d3-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a9d3-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a9d3-145">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a9d3-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a9d3-146">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a9d3-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a9d3-147">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a9d3-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9d3-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a9d3-148">See Also</span></span>  
 [<span data-ttu-id="0a9d3-149">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a9d3-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="0a9d3-150">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0a9d3-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
