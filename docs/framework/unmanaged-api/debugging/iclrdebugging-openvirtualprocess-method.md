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
ms.openlocfilehash: a313ea62455067fb36b94d942b0ce21589677e3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122580"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="6d27d-102">ICLRDebugging::OpenVirtualProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d27d-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="6d27d-103">Pobiera icordebugprocess — interfejs, który odnosi się do wspólnego języka wspólnego (CLR) moduł załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="6d27d-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d27d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d27d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6d27d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d27d-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="6d27d-106">[in] Adres podstawowy moduł w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="6d27d-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="6d27d-107">COR_E_NOT_CLR zostanie zwrócona, jeśli określony moduł nie jest modułem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6d27d-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="6d27d-108">[in] Abstrakcja docelowego danych, umożliwiająca zarządzanego debugera sprawdzić stan procesu.</span><span class="sxs-lookup"><span data-stu-id="6d27d-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="6d27d-109">Debuger musi implementować [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6d27d-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="6d27d-110">Należy zaimplementować [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu do obsługi scenariuszy, w których CLR, która jest debugowana nie zainstalowano lokalnie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6d27d-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="6d27d-111">[in] Biblioteka dostawcy interfejs wywołania zwrotnego, która umożliwia bibliotekom debudowania określonych wersji lokalizowanie i ładowanie na żądanie.</span><span class="sxs-lookup"><span data-stu-id="6d27d-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="6d27d-112">Ten parametr jest wymagany tylko wtedy, gdy `ppProcess` lub `pFlags` nie `null`.</span><span class="sxs-lookup"><span data-stu-id="6d27d-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="6d27d-113">[in] Najnowsza wersja środowiska CLR, który można debugować ten debuger.</span><span class="sxs-lookup"><span data-stu-id="6d27d-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="6d27d-114">Należy określić głównych i pomocniczych i tworzenia wersji z najnowszej wersji środowiska CLR, który obsługuje ten debuger i ustawić numer poprawki do 65535, aby pomieścić przyszłych CLR w miejscu, obsługi wersji.</span><span class="sxs-lookup"><span data-stu-id="6d27d-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="6d27d-115">[in] Identyfikator icordebugprocess — interfejs do pobrania.</span><span class="sxs-lookup"><span data-stu-id="6d27d-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="6d27d-116">Obecnie tylko akceptowane wartości są IID_CORDEBUGPROCESS3 IID_CORDEBUGPROCESS2 i IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="6d27d-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="6d27d-117">[out] Wskaźnik do interfejsu COM, który jest identyfikowany przez `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="6d27d-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="6d27d-118">[out w] Wersja środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6d27d-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="6d27d-119">W danych wejściowych, ta wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="6d27d-119">On input, this value can be `null`.</span></span> <span data-ttu-id="6d27d-120">Może też wskazywać na [clr_debugging_version —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) strukturę, w którym to przypadku struktury `wStructVersion` pola musi zostać zainicjowany do 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="6d27d-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="6d27d-121">W danych wyjściowych, zwrócony `CLR_DEBUGGING_VERSION` struktury zostanie wypełniona informacje o wersji dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6d27d-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="6d27d-122">[out] Flagi informacyjne dotyczące określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6d27d-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="6d27d-123">Zobacz [clr_debugging_process_flags —](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tematu, aby uzyskać opis flag.</span><span class="sxs-lookup"><span data-stu-id="6d27d-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d27d-124">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6d27d-124">Return Value</span></span>  
 <span data-ttu-id="6d27d-125">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6d27d-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6d27d-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d27d-126">HRESULT</span></span>|<span data-ttu-id="6d27d-127">Opis</span><span class="sxs-lookup"><span data-stu-id="6d27d-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d27d-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d27d-128">S_OK</span></span>|<span data-ttu-id="6d27d-129">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6d27d-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="6d27d-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6d27d-130">E_POINTER</span></span>|<span data-ttu-id="6d27d-131">`pDataTarget` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6d27d-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="6d27d-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="6d27d-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="6d27d-133">[Iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) wywołania zwrotnego zwraca błąd lub nie zawiera prawidłowego uchwytu.</span><span class="sxs-lookup"><span data-stu-id="6d27d-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="6d27d-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="6d27d-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="6d27d-135">`pDataTarget` nie implementuje interfejsy docelowym wymagane dane dla tej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6d27d-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="6d27d-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="6d27d-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="6d27d-137">Wskazany modułu nie jest modułem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6d27d-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="6d27d-138">Ta wartość HRESULT jest także zwracany, jeśli nie można wykryć moduł CLR, ponieważ została uszkodzona pamięć, moduł nie jest dostępna lub wersja środowiska CLR jest nowsza niż wersja podkładki.</span><span class="sxs-lookup"><span data-stu-id="6d27d-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="6d27d-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="6d27d-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="6d27d-140">Ta wersja środowiska uruchomieniowego nie obsługuje debugowania modelu.</span><span class="sxs-lookup"><span data-stu-id="6d27d-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="6d27d-141">Obecnie debugowania model nie jest obsługiwany przez wersje środowiska CLR przed [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d27d-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6d27d-142">`pwszVersion` Parametru wyjściowego nadal jest ustawione na prawidłową wartość po tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="6d27d-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="6d27d-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="6d27d-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="6d27d-144">Wersja środowiska CLR jest nowsza niż wersja, ten debuger oświadczenia do obsługi.</span><span class="sxs-lookup"><span data-stu-id="6d27d-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="6d27d-145">`pwszVersion` Parametru wyjściowego nadal jest ustawione na prawidłową wartość po tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="6d27d-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="6d27d-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="6d27d-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="6d27d-147">`riidProcess` Interfejs nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="6d27d-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="6d27d-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="6d27d-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="6d27d-149">`CLR_DEBUGGING_VERSION` Struktura ma rozpoznawaną wartością dla `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="6d27d-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="6d27d-150">To jedyna wartość zaakceptowane w tej chwili to 0.</span><span class="sxs-lookup"><span data-stu-id="6d27d-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6d27d-151">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="6d27d-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d27d-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d27d-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d27d-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d27d-153">Requirements</span></span>  
 <span data-ttu-id="6d27d-154">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d27d-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d27d-155">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d27d-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d27d-156">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d27d-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d27d-157">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d27d-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d27d-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d27d-158">See also</span></span>

- [<span data-ttu-id="6d27d-159">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d27d-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6d27d-160">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6d27d-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
