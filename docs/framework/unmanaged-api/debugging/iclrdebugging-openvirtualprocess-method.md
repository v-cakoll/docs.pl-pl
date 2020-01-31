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
ms.openlocfilehash: 585b3d605d0df9169c12ca10198846ec0a7fe6d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793607"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="22993-102">ICLRDebugging::OpenVirtualProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="22993-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="22993-103">Pobiera interfejs ICorDebugProcess, który odnosi się do modułu środowiska uruchomieniowego języka wspólnego (CLR) załadowanego w procesie.</span><span class="sxs-lookup"><span data-stu-id="22993-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22993-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22993-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="22993-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22993-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="22993-106">podczas Adres podstawowy modułu w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="22993-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="22993-107">COR_E_NOT_CLR będzie zwracana, jeśli określony moduł nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="22993-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="22993-108">podczas Abstrakcja elementu docelowego danych umożliwiająca zarządzanemu debugerowi sprawdzenie stanu procesu.</span><span class="sxs-lookup"><span data-stu-id="22993-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="22993-109">Debuger musi implementować interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="22993-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="22993-110">Należy zaimplementować interfejs [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , aby obsługiwał scenariusze, w których DEBUGOWANE środowisko CLR nie jest zainstalowane lokalnie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="22993-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="22993-111">podczas Interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji na żądanie.</span><span class="sxs-lookup"><span data-stu-id="22993-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="22993-112">Ten parametr jest wymagany tylko wtedy, gdy nie `null``ppProcess` lub `pFlags`.</span><span class="sxs-lookup"><span data-stu-id="22993-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="22993-113">podczas Największa wersja środowiska CLR, którą może debugować ten debuger.</span><span class="sxs-lookup"><span data-stu-id="22993-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="22993-114">Należy określić wersje główne, pomocnicze i kompilacje od najnowszej wersji środowiska CLR obsługiwane przez ten debuger i ustawić numer poprawki na 65535 w celu uwzględnienia przyszłych wydań obsługi środowiska CLR w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="22993-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="22993-115">podczas Identyfikator interfejsu ICorDebugProcess do pobrania.</span><span class="sxs-lookup"><span data-stu-id="22993-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="22993-116">Obecnie Jedyne akceptowane wartości to IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 i IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="22993-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="22993-117">określoną Wskaźnik do interfejsu COM, który jest identyfikowany przez `riidProcess`.</span><span class="sxs-lookup"><span data-stu-id="22993-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="22993-118">[in. out] Wersja środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="22993-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="22993-119">Na wejściu ta wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="22993-119">On input, this value can be `null`.</span></span> <span data-ttu-id="22993-120">Może również wskazywać na strukturę [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) , w którym przypadku pole `wStructVersion` struktury musi być inicjowane na wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="22993-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="22993-121">W danych wyjściowych, zwrócona struktura `CLR_DEBUGGING_VERSION` zostanie wypełniona informacjami o wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="22993-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="22993-122">określoną Flagi informacyjne dotyczące określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="22993-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="22993-123">Opis flag można znaleźć w temacie [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="22993-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22993-124">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="22993-124">Return Value</span></span>  
 <span data-ttu-id="22993-125">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="22993-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="22993-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22993-126">HRESULT</span></span>|<span data-ttu-id="22993-127">Opis</span><span class="sxs-lookup"><span data-stu-id="22993-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22993-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="22993-128">S_OK</span></span>|<span data-ttu-id="22993-129">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="22993-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="22993-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="22993-130">E_POINTER</span></span>|<span data-ttu-id="22993-131">`pDataTarget` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="22993-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="22993-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="22993-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="22993-133">Wywołanie zwrotne [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) zwraca błąd lub nie zapewnia prawidłowego dojścia.</span><span class="sxs-lookup"><span data-stu-id="22993-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="22993-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="22993-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="22993-135">`pDataTarget` nie implementuje wymaganych interfejsów obiektów docelowych danych dla tej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="22993-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="22993-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="22993-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="22993-137">Wskazany moduł nie jest modułem CLR.</span><span class="sxs-lookup"><span data-stu-id="22993-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="22993-138">Ten wynik HRESULT jest również zwracany, gdy nie można wykryć modułu CLR, ponieważ pamięć została uszkodzona, moduł jest niedostępny lub wersja środowiska CLR jest nowsza niż wersja podkładki.</span><span class="sxs-lookup"><span data-stu-id="22993-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="22993-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="22993-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="22993-140">Ta wersja środowiska uruchomieniowego nie obsługuje tego modelu debugowania.</span><span class="sxs-lookup"><span data-stu-id="22993-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="22993-141">Obecnie model debugowania nie jest obsługiwany przez wersje środowiska CLR przed .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22993-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="22993-142">Parametr danych wyjściowych `pwszVersion` nadal jest ustawiany na poprawną wartość po wystąpieniu tego błędu.</span><span class="sxs-lookup"><span data-stu-id="22993-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="22993-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="22993-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="22993-144">Wersja środowiska CLR jest nowsza niż wersja tego debugera do obsługi.</span><span class="sxs-lookup"><span data-stu-id="22993-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="22993-145">Parametr danych wyjściowych `pwszVersion` nadal jest ustawiany na poprawną wartość po wystąpieniu tego błędu.</span><span class="sxs-lookup"><span data-stu-id="22993-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="22993-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="22993-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="22993-147">Interfejs `riidProcess` nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="22993-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="22993-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="22993-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="22993-149">Struktura `CLR_DEBUGGING_VERSION` nie ma rozpoznawanej wartości dla `wStructVersion`.</span><span class="sxs-lookup"><span data-stu-id="22993-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="22993-150">Jedyną akceptowaną wartością w tym momencie jest 0.</span><span class="sxs-lookup"><span data-stu-id="22993-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="22993-151">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="22993-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22993-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22993-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22993-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22993-153">Requirements</span></span>  
 <span data-ttu-id="22993-154">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22993-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22993-155">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22993-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22993-156">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="22993-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22993-157">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22993-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22993-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22993-158">See also</span></span>

- [<span data-ttu-id="22993-159">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="22993-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="22993-160">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="22993-160">Debugging</span></span>](index.md)
