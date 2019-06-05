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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b45efb634ca9b88768d6e30884085f28ad17b7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490589"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="67745-102">CorBindToRuntimeEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="67745-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="67745-103">Włącza niezarządzane hosty do załadowania środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="67745-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="67745-104">[CorBindToRuntime —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) i `CorBindToRuntimeEx` funkcje wykonują tę samą operację, ale `CorBindToRuntimeEx` funkcja pozwala na ustawienie flagi, aby określić zachowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="67745-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="67745-105">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67745-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="67745-106">Ta funkcja pobiera zestaw parametrów, zezwalających na hoście, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="67745-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="67745-107">Określ wersję środowiska uruchomieniowego, które będą ładowane.</span><span class="sxs-lookup"><span data-stu-id="67745-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="67745-108">Wskazuje, czy serwer lub stacja robocza kompilacji powinny być załadowane.</span><span class="sxs-lookup"><span data-stu-id="67745-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="67745-109">Kontrolowanie, czy współbieżne wyrzucanie elementów bezużytecznych lub niewspółbieżnym wyrzucaniem elementów bezużytecznych jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="67745-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67745-110">Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwana w aplikacjach działających w emulatorze WOW64 x86 emulatora w systemach 64-bitowych, które implementują architekturę Intel Itanium (wcześniej noszącą nazwę IA-64).</span><span class="sxs-lookup"><span data-stu-id="67745-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="67745-111">Aby uzyskać więcej informacji o używaniu WOW64 w 64-bitowych systemach Windows, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="67745-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="67745-112">Kontrolowanie, czy zestawy są ładowane jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="67745-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="67745-113">Wskaźnik interfejsu do uzyskania [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) można ustawić dodatkowe opcje dotyczące konfigurowania wystąpienia środowiska CLR, przed jej ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="67745-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67745-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="67745-114">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67745-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="67745-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="67745-116">[in] Ciąg opisujący wersję środowiska CLR chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="67745-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="67745-117">Numer wersji w programie .NET Framework składa się z czterech części oddzielonych kropkami: *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="67745-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="67745-118">Ciąg przekazany jako `pwszVersion` musi zaczynać się od znaków "v", następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="67745-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="67745-119">Niektóre wersje środowiska CLR są instalowane z deklaracji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="67745-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="67745-120">Domyślnie, uruchomienie podkładki programowej ocenia `pwszVersion` wobec deklaracji i obciążeń najnowszej wersji środowiska uruchomieniowego, jest zgodny z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="67745-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="67745-121">Host może wymusić podkładkę, aby pominąć zasady oceny i załadować dokładną wersję określoną w `pwszVersion` , przekazując wartość `STARTUP_LOADER_SAFEMODE` dla `startupFlags` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="67745-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="67745-122">Jeśli obiekt wywołujący określa wartość null w przypadku `pwszVersion`, `CorBindToRuntimeEx` identyfikuje zestaw zainstalowanego środowiska uruchomieniowe, których numery wersji są niższe niż w środowisku uruchomieniowym .NET Framework 4 i ładuje najnowszą wersję środowiska uruchomieniowego z tego zbioru.</span><span class="sxs-lookup"><span data-stu-id="67745-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="67745-123">Nie będzie on ładować .NET Framework 4 lub nowszy, a kończy się niepowodzeniem, jeśli zainstalowano nie wcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="67745-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="67745-124">Należy zauważyć, że przekazywanie wartości null daje hosta bez kontroli nad tym, którzy wersja środowiska uruchomieniowego jest załadowana.</span><span class="sxs-lookup"><span data-stu-id="67745-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="67745-125">Mimo że takie podejście może być odpowiedni w niektórych scenariuszach, zdecydowanie zaleca się że host podać do załadowania określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="67745-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="67745-126">[in] Ciąg, który określa, czy ładować serwer czy stację roboczą kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="67745-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="67745-127">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="67745-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="67745-128">Server kompilacji jest zoptymalizowany, aby móc korzystać z wielu procesorów do wyrzucania elementów bezużytecznych, a stacja robocza kompilacji jest zoptymalizowany dla aplikacji klienckich działających na komputerze jednoprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="67745-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="67745-129">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, stacja robocza kompilacji jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="67745-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="67745-130">Podczas uruchamiania na komputerze jednoprocesorowym, stacja robocza kompilacji będzie zawsze ładowana, nawet jeśli `pwszBuildFlavor` ustawiono `svr`.</span><span class="sxs-lookup"><span data-stu-id="67745-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="67745-131">Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i współbieżne wyrzucanie elementów bezużytecznych zostało określone (zobacz opis `startupFlags` parametru), ładowana jest kompilacja serwera.</span><span class="sxs-lookup"><span data-stu-id="67745-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="67745-132">[in] Kombinacja wartości [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="67745-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="67745-133">Te flagi kontrolować współbieżne wyrzucanie elementów bezużytecznych, kodem domeny neutralnej i zachowaniem `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="67745-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="67745-134">Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="67745-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="67745-135">Następujące wartości są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="67745-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="67745-136">Aby uzyskać opis tych flag, zobacz [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="67745-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="67745-137">[in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="67745-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="67745-138">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="67745-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="67745-139">[in] `IID` Żądanego interfejsu z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="67745-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="67745-140">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="67745-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="67745-141">[out] Wskaźnik interfejsu zwrócone do `riid`.</span><span class="sxs-lookup"><span data-stu-id="67745-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67745-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67745-142">Remarks</span></span>  
 <span data-ttu-id="67745-143">Jeśli `pwszVersion` Określa wersję środowiska uruchomieniowego, który nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="67745-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="67745-144">Kontekstu wykonywania i przepływ tożsamości Windows</span><span class="sxs-lookup"><span data-stu-id="67745-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="67745-145">W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> obiektu nie przepływać przez punkty asynchroniczne, takie jak nowe wątki, pul wątków lub czasomierza wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="67745-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="67745-146">W wersji 2.0 środowisko CLR <xref:System.Threading.ExecutionContext> obiektu otacza pewne informacje o aktualnie wykonywany wątek i przepływy go między kiedykolwiek asynchronicznego, ale nie granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67745-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="67745-147">Podobnie <xref:System.Security.Principal.WindowsIdentity> obiektu również odbywa się za pośrednictwem dowolnego punktu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="67745-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="67745-148">W związku z tym bieżący personifikacji w wątku, ewentualnie przepływów zbyt.</span><span class="sxs-lookup"><span data-stu-id="67745-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="67745-149">Można zmienić przepływ na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="67745-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="67745-150">Modyfikując <xref:System.Threading.ExecutionContext> ustawienia, aby wstrzymać przepływ na podstawie na wątek (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="67745-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="67745-151">Po zmianie procesu domyślny tryb na tryb zgodności w wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu w dowolnym momencie asynchronicznego niezależnie od wartości <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="67745-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="67745-152">Jak zmienić domyślny tryb, zależy od tego, czy używać zarządzanego pliku wykonywalnego lub niezarządzanego interfejsu hostingu do ładowania CLR:</span><span class="sxs-lookup"><span data-stu-id="67745-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="67745-153">Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="67745-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="67745-154">W przypadku niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` znacznik w `startupFlags` parametru podczas wywoływania `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="67745-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="67745-155">Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="67745-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67745-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67745-156">Requirements</span></span>  
 <span data-ttu-id="67745-157">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67745-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67745-158">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="67745-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67745-159">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67745-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67745-160">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67745-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67745-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67745-161">See also</span></span>

- [<span data-ttu-id="67745-162">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="67745-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="67745-163">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="67745-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="67745-164">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="67745-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="67745-165">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="67745-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="67745-166">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="67745-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="67745-167">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="67745-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
