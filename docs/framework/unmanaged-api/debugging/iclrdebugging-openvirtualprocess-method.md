---
title: ICLRDebugging::OpenVirtualProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51b5a9ecd85f0d40ac2fe2826cbbe7a56a6228d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408255"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="a03e8-102">ICLRDebugging::OpenVirtualProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="a03e8-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="a03e8-103">Pobiera interfejs ICorDebugProcess, który odpowiada wspólny języka wspólnego (CLR) moduł załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="a03e8-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a03e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a03e8-104">Syntax</span></span>  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a03e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a03e8-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="a03e8-106">[in] Adres podstawowy modułu w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="a03e8-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="a03e8-107">COR_E_NOT_CLR zostanie zwrócony, jeśli określony moduł nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="a03e8-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="a03e8-108">[in] Abstrakcja docelowego danych, umożliwiający zarządzanego debugera sprawdzić stan procesu.</span><span class="sxs-lookup"><span data-stu-id="a03e8-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="a03e8-109">Debuger musi implementować [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a03e8-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="a03e8-110">Należy zaimplementować [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejs na potrzeby obsługi scenariuszy, których CLR, która jest debugowany nie zainstalowano lokalnie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a03e8-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="a03e8-111">[in] Biblioteka dostawcy wywołanie zwrotne interfejsu, który umożliwia bibliotek debugowania określonej wersji, należy odnaleźć i załadować na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a03e8-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="a03e8-112">Ten parametr jest wymagany tylko wtedy, gdy `ppProcess` lub `pFlags` nie jest `null`.</span><span class="sxs-lookup"><span data-stu-id="a03e8-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="a03e8-113">[in] Najwyższa wersja środowiska CLR, która może debugować ten debuger.</span><span class="sxs-lookup"><span data-stu-id="a03e8-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="a03e8-114">Należy określić głównych i pomocniczych i kompilacji wersji z najnowszej wersji środowiska CLR, który obsługuje ten debuger i ustawiony numer poprawki do 65535, aby zmieścił się w przyszłości CLR w miejscu obsługi wersji.</span><span class="sxs-lookup"><span data-stu-id="a03e8-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="a03e8-115">[in] Identyfikator interfejsu ICorDebugProcess do pobrania.</span><span class="sxs-lookup"><span data-stu-id="a03e8-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="a03e8-116">Obecnie akceptowane wartości to wyłącznie są IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 i IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="a03e8-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a03e8-117">[out] Wskaźnik do interfejsu COM, który jest identyfikowany przez `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="a03e8-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a03e8-118">[w, out] Wersja środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a03e8-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="a03e8-119">W danych wejściowych, ta wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="a03e8-119">On input, this value can be `null`.</span></span> <span data-ttu-id="a03e8-120">Może także wskazywać [clr_debugging_version —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) struktury, w którym to przypadku struktury `wStructVersion` pola musi zostać zainicjowany jako 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="a03e8-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="a03e8-121">W danych wyjściowych, zwracana `CLR_DEBUGGING_VERSION` struktury zostaną wypełnione informacje o wersji dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a03e8-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="a03e8-122">[out] Informacyjny flagi informacje o określonym środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="a03e8-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="a03e8-123">Zobacz [clr_debugging_process_flags —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) temacie opis flag.</span><span class="sxs-lookup"><span data-stu-id="a03e8-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a03e8-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a03e8-124">Return Value</span></span>  
 <span data-ttu-id="a03e8-125">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a03e8-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a03e8-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a03e8-126">HRESULT</span></span>|<span data-ttu-id="a03e8-127">Opis</span><span class="sxs-lookup"><span data-stu-id="a03e8-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a03e8-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="a03e8-128">S_OK</span></span>|<span data-ttu-id="a03e8-129">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a03e8-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="a03e8-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a03e8-130">E_POINTER</span></span>|<span data-ttu-id="a03e8-131">`pDataTarget` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="a03e8-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="a03e8-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="a03e8-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="a03e8-133">[Iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) wywołania zwrotnego zwraca błąd lub nie ma prawidłowego dojścia.</span><span class="sxs-lookup"><span data-stu-id="a03e8-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="a03e8-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="a03e8-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="a03e8-135">`pDataTarget` nie implementuje interfejsów docelowy wymagane dane dla tej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a03e8-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="a03e8-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="a03e8-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="a03e8-137">Wskazany modułu nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="a03e8-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="a03e8-138">Ta wartość HRESULT jest także zwracany, jeśli nie można wykryć modułu CLR, ponieważ uszkodzona pamięć, moduł nie jest dostępna lub wersja środowiska CLR jest nowsza niż wersja podkładki.</span><span class="sxs-lookup"><span data-stu-id="a03e8-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="a03e8-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="a03e8-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="a03e8-140">Ta wersja środowiska uruchomieniowego nie obsługuje ten model debugowania.</span><span class="sxs-lookup"><span data-stu-id="a03e8-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="a03e8-141">Obecnie model debugowania nie jest obsługiwany przez wersje CLR przed [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a03e8-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a03e8-142">`pwszVersion` Parametr wyjściowy nadal jest ustawione na prawidłową wartość po tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="a03e8-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="a03e8-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="a03e8-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="a03e8-144">Wersja środowiska CLR jest nowsza niż wersja, ten debuger oświadczenia do obsługi.</span><span class="sxs-lookup"><span data-stu-id="a03e8-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="a03e8-145">`pwszVersion` Parametr wyjściowy nadal jest ustawione na prawidłową wartość po tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="a03e8-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="a03e8-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="a03e8-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="a03e8-147">`riidProcess` Interfejs nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="a03e8-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="a03e8-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="a03e8-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="a03e8-149">`CLR_DEBUGGING_VERSION` Struktury nie ma rozpoznawaną wartością dla `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="a03e8-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="a03e8-150">Wartość akceptowane tylko w tej chwili jest 0.</span><span class="sxs-lookup"><span data-stu-id="a03e8-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a03e8-151">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="a03e8-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a03e8-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a03e8-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a03e8-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a03e8-153">Requirements</span></span>  
 <span data-ttu-id="a03e8-154">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a03e8-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a03e8-155">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a03e8-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a03e8-156">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a03e8-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a03e8-157">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a03e8-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03e8-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a03e8-158">See Also</span></span>  
 [<span data-ttu-id="a03e8-159">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a03e8-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a03e8-160">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a03e8-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
