---
title: CorBindToRuntime — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 0bcfe42a70d64c091851a1eec81d03e49dbde52b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616675"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="d4e44-102">CorBindToRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d4e44-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="d4e44-103">Umożliwia niezarządzanym hostom ładowanie środowiska uruchomieniowego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="d4e44-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="d4e44-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d4e44-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e44-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4e44-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4e44-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4e44-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="d4e44-107">podczas Ciąg opisujący wersję środowiska CLR, które chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="d4e44-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="d4e44-108">Numer wersji w .NET Framework składa się z czterech części oddzielonych kropkami: *główna. pomocnicza. kompilacja. poprawka*.</span><span class="sxs-lookup"><span data-stu-id="d4e44-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="d4e44-109">Ciąg przeszedł jako `pwszVersion` musi rozpoczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="d4e44-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="d4e44-110">Niektóre wersje środowiska CLR są instalowane z instrukcją zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d4e44-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="d4e44-111">Domyślnie podkładka uruchamiania szacuje się `pwszVersion` przed instrukcjami zasad i ładuje najnowszą wersję środowiska uruchomieniowego, która jest zgodna z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="d4e44-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="d4e44-112">Host może zmusić podkładkę do pominięcia oceny zasad i załadować dokładną wersję określoną w `pwszVersion` przez przekazanie wartości `STARTUP_LOADER_SAFEMODE` `flags` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="d4e44-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="d4e44-113">Jeśli obiekt wywołujący określa wartość null dla `pwszVersion` , zostanie załadowana Najnowsza wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d4e44-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="d4e44-114">Przekazanie wartości null powoduje, że host nie kontroluje, która wersja środowiska uruchomieniowego jest załadowana.</span><span class="sxs-lookup"><span data-stu-id="d4e44-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="d4e44-115">Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby Host dostarczał określoną wersję do załadowania.</span><span class="sxs-lookup"><span data-stu-id="d4e44-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="d4e44-116">podczas Ciąg określający, czy załadować serwer lub kompilację stacji roboczej środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d4e44-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="d4e44-117">Prawidłowe wartości to `svr` i `wks` .</span><span class="sxs-lookup"><span data-stu-id="d4e44-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="d4e44-118">Kompilacja serwera jest zoptymalizowana pod kątem wykorzystania wielu procesorów na potrzeby wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.</span><span class="sxs-lookup"><span data-stu-id="d4e44-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="d4e44-119">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="d4e44-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="d4e44-120">W przypadku uruchamiania na komputerze z jednym procesorem kompilacja stacji roboczej jest zawsze ładowana, nawet jeśli `pwszBuildFlavor` jest ustawiona na `svr` .</span><span class="sxs-lookup"><span data-stu-id="d4e44-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="d4e44-121">Jeśli jednak `pwszBuildFlavor` jest ustawiona na `svr` i zostanie określone współbieżne wyrzucanie elementów bezużytecznych (zobacz Opis `flags` parametru), kompilacja serwera zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="d4e44-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="d4e44-122">podczas `CLSID`Klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d4e44-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="d4e44-123">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="d4e44-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="d4e44-124">podczas `IID`Żądany interfejs z `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="d4e44-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="d4e44-125">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="d4e44-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="d4e44-126">określoną Zwrócony wskaźnik interfejsu do `riid` .</span><span class="sxs-lookup"><span data-stu-id="d4e44-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4e44-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4e44-127">Remarks</span></span>  
 <span data-ttu-id="d4e44-128">Jeśli `pwszVersion` określa wersję środowiska uruchomieniowego, która nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="d4e44-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="d4e44-129">Kontekst wykonywania i przepływ tożsamości systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d4e44-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="d4e44-130">W wersji 1 środowiska CLR <xref:System.Security.Principal.WindowsIdentity> obiekt nie przepływa między punktami asynchronicznymi, takimi jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza.</span><span class="sxs-lookup"><span data-stu-id="d4e44-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="d4e44-131">W wersji 2,0 środowiska CLR <xref:System.Threading.ExecutionContext> Obiekt otacza pewne informacje o aktualnie wykonywanym wątku i przepływa go w dowolnym punkcie asynchronicznym, ale nie między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4e44-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="d4e44-132">Podobnie obiekt jest <xref:System.Security.Principal.WindowsIdentity> również przepływny w każdym punkcie asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="d4e44-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="d4e44-133">W związku z tym bieżąca personifikacja w wątku, jeśli istnieje, również przepływów.</span><span class="sxs-lookup"><span data-stu-id="d4e44-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="d4e44-134">Przepływ można zmienić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="d4e44-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="d4e44-135">Modyfikując <xref:System.Threading.ExecutionContext> Ustawienia, aby pominąć przepływ dla poszczególnych wątków (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> metody,, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="d4e44-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="d4e44-136">Poprzez zmianę trybu domyślnego procesu na tryb zgodności w wersji 1, gdzie obiekt nie jest <xref:System.Security.Principal.WindowsIdentity> przepływem w żadnym punkcie asynchronicznym, niezależnie od <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="d4e44-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="d4e44-137">Sposób zmiany trybu domyślnego zależy od tego, czy do załadowania środowiska CLR jest używany zarządzany plik wykonywalny, czy niezarządzany interfejs hostingu:</span><span class="sxs-lookup"><span data-stu-id="d4e44-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="d4e44-138">W przypadku zarządzanych plików wykonywalnych należy ustawić `enabled` atrybut [ \< legacyImpersonationPolicy elementu>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="d4e44-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="d4e44-139">W przypadku niezarządzanych interfejsów hostingu Ustaw `STARTUP_LEGACY_IMPERSONATION` flagę w `flags` parametrze podczas wywoływania `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d4e44-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="d4e44-140">Tryb zgodności w wersji 1 dotyczy całego procesu i wszystkich domen aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="d4e44-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4e44-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4e44-141">Remarks</span></span>  
 <span data-ttu-id="d4e44-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) i `CorBindToRuntime` Wykonaj tę samą operację, ale `CorBindToRuntimeEx` Funkcja pozwala ustawić flagi, aby określić zachowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d4e44-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e44-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4e44-143">Requirements</span></span>  
 <span data-ttu-id="d4e44-144">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4e44-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e44-145">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4e44-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4e44-146">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4e44-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4e44-147">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e44-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e44-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4e44-148">See also</span></span>

- [<span data-ttu-id="d4e44-149">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="d4e44-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="d4e44-150">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d4e44-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="d4e44-151">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="d4e44-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="d4e44-152">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d4e44-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="d4e44-153">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4e44-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="d4e44-154">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d4e44-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
