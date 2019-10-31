---
title: ICorDebugModule — Interfejs
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
ms.openlocfilehash: 971d6a6a2157c48dcb9105e9f523b1f077098479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129488"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="a1e96-102">ICorDebugModule — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1e96-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="a1e96-103">Reprezentuje moduł środowiska uruchomieniowego języka wspólnego (CLR), który jest plikiem wykonywalnym lub biblioteką dołączaną dynamicznie (DLL).</span><span class="sxs-lookup"><span data-stu-id="a1e96-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1e96-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1e96-104">Methods</span></span>  
  
|<span data-ttu-id="a1e96-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-105">Method</span></span>|<span data-ttu-id="a1e96-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a1e96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1e96-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="a1e96-108">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="a1e96-108">Not implemented.</span></span>|  
|[<span data-ttu-id="a1e96-109">EnableClassLoadCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="a1e96-110">Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="a1e96-111">EnableJITDebugging, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="a1e96-112">Określa, czy kompilator just in Time (JIT) zachowuje informacje debugowania dla metod w ramach tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="a1e96-113">GetAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="a1e96-114">Pobiera zawierający go zestaw dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="a1e96-115">GetBaseAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="a1e96-116">Pobiera adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="a1e96-117">GetClassFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="a1e96-118">Pobiera ICorDebugClass z metadanych.</span><span class="sxs-lookup"><span data-stu-id="a1e96-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="a1e96-119">GetEditAndContinueSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="a1e96-120">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="a1e96-120">Deprecated.</span></span>|  
|[<span data-ttu-id="a1e96-121">GetFunctionFromRVA, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="a1e96-122">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="a1e96-122">Not implemented.</span></span>|  
|[<span data-ttu-id="a1e96-123">GetFunctionFromToken, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="a1e96-124">Pobiera funkcję określoną przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="a1e96-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="a1e96-125">GetGlobalVariableValue, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="a1e96-126">Pobiera obiekt wartości dla określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="a1e96-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="a1e96-127">GetMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="a1e96-128">Pobiera wskaźnik interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="a1e96-129">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="a1e96-130">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="a1e96-131">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="a1e96-132">Pobiera proces zawierający dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="a1e96-133">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="a1e96-134">Pobiera rozmiar modułu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a1e96-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="a1e96-135">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="a1e96-136">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a1e96-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="a1e96-137">IsDynamic, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="a1e96-138">Wskazuje, czy moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="a1e96-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="a1e96-139">IsInMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="a1e96-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="a1e96-140">Wskazuje, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a1e96-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1e96-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1e96-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1e96-142">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a1e96-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e96-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1e96-143">Requirements</span></span>  
 <span data-ttu-id="a1e96-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e96-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e96-145">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1e96-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1e96-146">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1e96-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1e96-147">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e96-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e96-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1e96-148">See also</span></span>

- [<span data-ttu-id="a1e96-149">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1e96-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="a1e96-150">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a1e96-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
