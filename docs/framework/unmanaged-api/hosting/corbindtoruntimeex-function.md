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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176503"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="9e397-102">CorBindToRuntimeEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9e397-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="9e397-103">Umożliwia hostów niezarządzanych załadować środowiska uruchomieniowego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="9e397-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="9e397-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) i `CorBindToRuntimeEx` funkcje wykonują tę `CorBindToRuntimeEx` samą operację, ale funkcja umożliwia ustawienie flagi, aby określić zachowanie CLR.</span><span class="sxs-lookup"><span data-stu-id="9e397-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="9e397-105">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9e397-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="9e397-106">Ta funkcja przyjmuje zestaw parametrów, które umożliwiają hostowi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9e397-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="9e397-107">Określ wersję środowiska wykonawczego, który zostanie załadowany.</span><span class="sxs-lookup"><span data-stu-id="9e397-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="9e397-108">Wskazać, czy ma zostać załadowana kompilacja serwera lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="9e397-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="9e397-109">Kontrolować, czy równoczesnych wyrzucania elementów bezużytecznych lub nie jednocześnie wyrzucania elementów bezużytecznych jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="9e397-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e397-110">Równoczesne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach z emulatorem WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej nazywaną IA-64).</span><span class="sxs-lookup"><span data-stu-id="9e397-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="9e397-111">Aby uzyskać więcej informacji na temat używania WOW64 w 64-bitowych systemach Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="9e397-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="9e397-112">Osłanianie, czy zestawy są ładowane jako neutralne dla domeny.</span><span class="sxs-lookup"><span data-stu-id="9e397-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="9e397-113">Uzyskaj wskaźnik interfejsu do [ICorRuntimeHost,](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) który może służyć do ustawiania dodatkowych opcji konfigurowania wystąpienia CLR przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="9e397-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e397-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e397-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9e397-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e397-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="9e397-116">[w] Ciąg opisujący wersję clr, który chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="9e397-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="9e397-117">Numer wersji w ramach .NET Framework składa się z czterech części oddzielonych kropkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="9e397-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="9e397-118">Ciąg przeszedł `pwszVersion` zgodnie z musi zaczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="9e397-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="9e397-119">Niektóre wersje programu CLR są instalowane z instrukcją zasad określającą zgodność z poprzednimi wersjami programu CLR.</span><span class="sxs-lookup"><span data-stu-id="9e397-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="9e397-120">Domyślnie podkładka uruchamiania `pwszVersion` ocenia instrukcje zasad i ładuje najnowszą wersję środowiska wykonawczego, która jest zgodna z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="9e397-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="9e397-121">Host może wymusić podkładkę do pominięcia oceny zasad `pwszVersion` i załadować `STARTUP_LOADER_SAFEMODE` dokładną wersję określoną przez przekazanie wartości parametru, `startupFlags` jak opisano poniżej.</span><span class="sxs-lookup"><span data-stu-id="9e397-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="9e397-122">Jeśli wywołujący określa wartość `pwszVersion` `CorBindToRuntimeEx` null dla , identyfikuje zestaw zainstalowanych runtimes których numery wersji są niższe niż .NET Framework 4 środowiska uruchomieniowego i ładuje najnowszą wersję środowiska wykonawczego z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9e397-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="9e397-123">Nie ładuje programu .NET Framework 4 lub nowszego i kończy się niepowodzeniem, jeśli nie zainstalowano żadnej wcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9e397-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="9e397-124">Należy zauważyć, że przekazywanie null daje hosta nie kontroli nad tym, która wersja środowiska wykonawczego jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="9e397-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="9e397-125">Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby host dostarczał określoną wersję do załadowania.</span><span class="sxs-lookup"><span data-stu-id="9e397-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="9e397-126">[w] Ciąg, który określa, czy załadować serwer lub kompilacji stacji roboczej CLR.</span><span class="sxs-lookup"><span data-stu-id="9e397-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="9e397-127">Prawidłowe `svr` wartości `wks`są i .</span><span class="sxs-lookup"><span data-stu-id="9e397-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="9e397-128">Kompilacja serwera jest zoptymalizowana pod kątem korzystania z wielu procesorów do wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.</span><span class="sxs-lookup"><span data-stu-id="9e397-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="9e397-129">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="9e397-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="9e397-130">Podczas pracy na komputerze z jednym procesorem kompilacja stacji `pwszBuildFlavor` roboczej `svr`jest zawsze ładowana, nawet jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="9e397-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="9e397-131">Jednak jeśli `pwszBuildFlavor` jest `svr` ustawiona i równoczesnych wyrzucania elementów `startupFlags` bezużytecznych jest określony (zobacz opis parametru), kompilacja serwera jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="9e397-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="9e397-132">[w] Kombinacja wartości wyliczenia [STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="9e397-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="9e397-133">Flagi te kontrolują równoczesnych wyrzucania elementów bezużytecznych, `pwszVersion` kod neutralny dla domeny i zachowanie parametru.</span><span class="sxs-lookup"><span data-stu-id="9e397-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="9e397-134">Wartość domyślna to pojedyncza domena, jeśli nie ustawiono żadnej flagi.</span><span class="sxs-lookup"><span data-stu-id="9e397-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="9e397-135">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="9e397-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="9e397-136">Opisy tych flag można znaleźć w [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9e397-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9e397-137">[w] Coclass, `CLSID` który implementuje interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9e397-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9e397-138">Obsługiwane wartości są CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9e397-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9e397-139">[w] Wymagany `IID` interfejs z . `rclsid`</span><span class="sxs-lookup"><span data-stu-id="9e397-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="9e397-140">Obsługiwane wartości są IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9e397-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9e397-141">[na zewnątrz] Zwrócony wskaźnik `riid`interfejsu do .</span><span class="sxs-lookup"><span data-stu-id="9e397-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e397-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e397-142">Remarks</span></span>  
 <span data-ttu-id="9e397-143">Jeśli `pwszVersion` określa wersję środowiska uruchomieniowego, `CorBindToRuntimeEx` która nie istnieje, zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="9e397-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="9e397-144">Kontekst wykonywania i przepływ tożsamości systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9e397-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="9e397-145">W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> obiekt nie przepływa przez punkty asynchroniczne, takie jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza.</span><span class="sxs-lookup"><span data-stu-id="9e397-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="9e397-146">W wersji 2.0 środowiska CLR obiekt zawija <xref:System.Threading.ExecutionContext> niektóre informacje o aktualnie wykonywanym wątku i przepływa przez dowolny punkt asynchroniczne, ale nie przez granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e397-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="9e397-147">Podobnie obiekt <xref:System.Security.Principal.WindowsIdentity> przepływa również przez dowolny punkt asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="9e397-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="9e397-148">W związku z tym bieżącej personifikacji w wątku, jeśli istnieje, przepływa zbyt.</span><span class="sxs-lookup"><span data-stu-id="9e397-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="9e397-149">Przepływ można zmienić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="9e397-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="9e397-150">Modyfikując <xref:System.Threading.ExecutionContext> ustawienia w celu wygaszenia przepływu <xref:System.Threading.ExecutionContext.SuppressFlow%2A>na <xref:System.Security.SecurityContext.SuppressFlow%2A>podstawie <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> wątku (patrz , i metody).</span><span class="sxs-lookup"><span data-stu-id="9e397-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="9e397-151">Zmieniając domyślny tryb procesu na tryb zgodności w wersji <xref:System.Security.Principal.WindowsIdentity> 1, w którym obiekt nie przepływa przez <xref:System.Threading.ExecutionContext> żaden punkt asynchroniczne, niezależnie od ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="9e397-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="9e397-152">Sposób zmiany trybu domyślnego zależy od tego, czy do załadowania programu CLR używasz zarządzanego pliku wykonywalnego, czy niezarządzanego interfejsu hostingu:</span><span class="sxs-lookup"><span data-stu-id="9e397-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="9e397-153">W przypadku zarządzanych plików wykonywalnych należy ustawić `enabled` atrybut [ \<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element na `true`.</span><span class="sxs-lookup"><span data-stu-id="9e397-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="9e397-154">W przypadku niezarządzanych interfejsów hostingu ustaw flagę `STARTUP_LEGACY_IMPERSONATION` w parametrze `startupFlags` podczas wywoływania `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9e397-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="9e397-155">Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i do wszystkich domen aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="9e397-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e397-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e397-156">Requirements</span></span>  
 <span data-ttu-id="9e397-157">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e397-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e397-158">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e397-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e397-159">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9e397-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e397-160">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e397-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e397-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e397-161">See also</span></span>

- [<span data-ttu-id="9e397-162">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="9e397-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9e397-163">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="9e397-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="9e397-164">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9e397-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9e397-165">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9e397-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9e397-166">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e397-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9e397-167">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="9e397-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
