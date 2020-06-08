---
title: CorBindToRuntimeEx — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
ms.openlocfilehash: e66b63ffa4ed25e861cff6bd9eb6065f57ff807f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493503"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="9a009-102">CorBindToRuntimeEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a009-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="9a009-103">Umożliwia niezarządzanym hostom ładowanie środowiska uruchomieniowego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="9a009-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="9a009-104">[CorBindToRuntime](corbindtoruntime-function.md) i `CorBindToRuntimeEx` funkcje wykonują tę samą operację, ale `CorBindToRuntimeEx` Funkcja pozwala ustawić flagi, aby określić zachowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9a009-104">The [CorBindToRuntime](corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="9a009-105">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9a009-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="9a009-106">Ta funkcja przyjmuje zestaw parametrów, które umożliwiają hostowi wykonywanie następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9a009-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="9a009-107">Określ wersję środowiska uruchomieniowego, która zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="9a009-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="9a009-108">Wskaż, czy należy załadować kompilację serwera lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="9a009-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="9a009-109">Określ, czy współbieżne odzyskiwanie pamięci lub niewspółbieżne wyrzucanie elementów bezużytecznych zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="9a009-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a009-110">Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach uruchamiających emulator WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej zwane IA-64).</span><span class="sxs-lookup"><span data-stu-id="9a009-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="9a009-111">Aby uzyskać więcej informacji na temat korzystania z emulatora WOW64 w systemach 64-bitowych systemu Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="9a009-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="9a009-112">Określ, czy zestawy są ładowane jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="9a009-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="9a009-113">Uzyskaj wskaźnik interfejsu do [ICorRuntimeHost](icorruntimehost-interface.md) , który może służyć do ustawiania dodatkowych opcji konfigurowania wystąpienia środowiska CLR przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="9a009-113">Obtain an interface pointer to an [ICorRuntimeHost](icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a009-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a009-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a009-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a009-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="9a009-116">podczas Ciąg opisujący wersję środowiska CLR, które chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="9a009-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="9a009-117">Numer wersji w .NET Framework składa się z czterech części oddzielonych kropkami: *główna. pomocnicza. kompilacja. poprawka*.</span><span class="sxs-lookup"><span data-stu-id="9a009-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="9a009-118">Ciąg przeszedł jako `pwszVersion` musi rozpoczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="9a009-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="9a009-119">Niektóre wersje środowiska CLR są instalowane z instrukcją zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9a009-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="9a009-120">Domyślnie podkładka uruchamiania szacuje się `pwszVersion` przed instrukcjami zasad i ładuje najnowszą wersję środowiska uruchomieniowego, która jest zgodna z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="9a009-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="9a009-121">Host może zmusić podkładkę do pominięcia oceny zasad i załadować dokładną wersję określoną w `pwszVersion` przez przekazanie wartości `STARTUP_LOADER_SAFEMODE` `startupFlags` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="9a009-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="9a009-122">Jeśli obiekt wywołujący określa wartość null dla programu `pwszVersion` , program `CorBindToRuntimeEx` zidentyfikuje zestaw zainstalowanych środowisk uruchomieniowych, których numery wersji są mniejsze niż środowisko uruchomieniowe .NET Framework 4 i ładuje najnowszą wersję środowiska uruchomieniowego z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9a009-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="9a009-123">Nie ładuje .NET Framework 4 lub nowszego i kończy się niepowodzeniem, jeśli nie jest zainstalowana wcześniejsza wersja.</span><span class="sxs-lookup"><span data-stu-id="9a009-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="9a009-124">Należy pamiętać, że przekazanie wartości null powoduje, że host nie kontroluje, która wersja środowiska uruchomieniowego jest załadowana.</span><span class="sxs-lookup"><span data-stu-id="9a009-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="9a009-125">Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby Host dostarczał określoną wersję do załadowania.</span><span class="sxs-lookup"><span data-stu-id="9a009-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="9a009-126">podczas Ciąg określający, czy załadować serwer lub kompilację stacji roboczej środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9a009-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="9a009-127">Prawidłowe wartości to `svr` i `wks` .</span><span class="sxs-lookup"><span data-stu-id="9a009-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="9a009-128">Kompilacja serwera jest zoptymalizowana pod kątem wykorzystania wielu procesorów na potrzeby wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.</span><span class="sxs-lookup"><span data-stu-id="9a009-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="9a009-129">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="9a009-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="9a009-130">W przypadku uruchamiania na komputerze z jednym procesorem kompilacja stacji roboczej jest zawsze ładowana, nawet jeśli `pwszBuildFlavor` jest ustawiona na `svr` .</span><span class="sxs-lookup"><span data-stu-id="9a009-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="9a009-131">Jeśli jednak `pwszBuildFlavor` jest ustawiona na `svr` i zostanie określone współbieżne wyrzucanie elementów bezużytecznych (zobacz Opis `startupFlags` parametru), kompilacja serwera zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="9a009-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="9a009-132">podczas Kombinacja wartości wyliczenia [STARTUP_FLAGS](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="9a009-132">[in] A combination of values of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="9a009-133">Flagi te kontrolują współbieżne wyrzucanie elementów bezużytecznych, kod neutralny przez domenę i zachowanie `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="9a009-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="9a009-134">Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="9a009-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="9a009-135">Następujące wartości są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="9a009-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="9a009-136">Opisy tych flag można znaleźć w temacie [STARTUP_FLAGS](startup-flags-enumeration.md) Enumeration.</span><span class="sxs-lookup"><span data-stu-id="9a009-136">For descriptions of these flags, see the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9a009-137">podczas `CLSID`Klasy coclass implementującej interfejs [ICorRuntimeHost](icorruntimehost-interface.md) lub [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9a009-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9a009-138">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9a009-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9a009-139">podczas `IID`Żądany interfejs z `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="9a009-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="9a009-140">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9a009-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9a009-141">określoną Zwrócony wskaźnik interfejsu do `riid` .</span><span class="sxs-lookup"><span data-stu-id="9a009-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a009-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a009-142">Remarks</span></span>  
 <span data-ttu-id="9a009-143">Jeśli `pwszVersion` określa wersję środowiska uruchomieniowego, która nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="9a009-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="9a009-144">Kontekst wykonywania i przepływ tożsamości systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9a009-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="9a009-145">W wersji 1 środowiska CLR <xref:System.Security.Principal.WindowsIdentity> obiekt nie przepływa między punktami asynchronicznymi, takimi jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza.</span><span class="sxs-lookup"><span data-stu-id="9a009-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="9a009-146">W wersji 2,0 środowiska CLR <xref:System.Threading.ExecutionContext> Obiekt otacza pewne informacje o aktualnie wykonywanym wątku i przepływa go w dowolnym punkcie asynchronicznym, ale nie między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a009-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="9a009-147">Podobnie obiekt jest <xref:System.Security.Principal.WindowsIdentity> również przepływny w każdym punkcie asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="9a009-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="9a009-148">W związku z tym bieżąca personifikacja w wątku, jeśli istnieje, również przepływów.</span><span class="sxs-lookup"><span data-stu-id="9a009-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="9a009-149">Przepływ można zmienić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="9a009-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="9a009-150">Modyfikując <xref:System.Threading.ExecutionContext> Ustawienia, aby pominąć przepływ dla poszczególnych wątków (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> metody,, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="9a009-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="9a009-151">Poprzez zmianę trybu domyślnego procesu na tryb zgodności w wersji 1, gdzie obiekt nie jest <xref:System.Security.Principal.WindowsIdentity> przepływem w żadnym punkcie asynchronicznym, niezależnie od <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="9a009-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="9a009-152">Sposób zmiany trybu domyślnego zależy od tego, czy do załadowania środowiska CLR jest używany zarządzany plik wykonywalny, czy niezarządzany interfejs hostingu:</span><span class="sxs-lookup"><span data-stu-id="9a009-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="9a009-153">W przypadku zarządzanych plików wykonywalnych należy ustawić `enabled` atrybut [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="9a009-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="9a009-154">W przypadku niezarządzanych interfejsów hostingu Ustaw `STARTUP_LEGACY_IMPERSONATION` flagę w `startupFlags` parametrze podczas wywoływania `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9a009-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="9a009-155">Tryb zgodności w wersji 1 dotyczy całego procesu i wszystkich domen aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="9a009-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a009-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a009-156">Requirements</span></span>  
 <span data-ttu-id="9a009-157">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a009-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a009-158">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a009-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a009-159">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a009-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a009-160">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a009-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a009-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a009-161">See also</span></span>

- [<span data-ttu-id="9a009-162">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="9a009-162">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9a009-163">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="9a009-163">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="9a009-164">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a009-164">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9a009-165">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a009-165">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="9a009-166">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a009-166">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="9a009-167">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="9a009-167">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
