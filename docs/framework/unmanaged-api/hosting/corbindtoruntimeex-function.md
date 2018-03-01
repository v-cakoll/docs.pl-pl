---
title: "CorBindToRuntimeEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c0080e5a01c8e856c2862182ba06096fdc9385c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="cb10d-102">CorBindToRuntimeEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="cb10d-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="cb10d-103">Umożliwia niezarządzane hosty załadować środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="cb10d-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="cb10d-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) i `CorBindToRuntimeEx` funkcje wykonać operację, ale `CorBindToRuntimeEx` funkcji można ustawić flagi, aby określić zachowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="cb10d-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="cb10d-105">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb10d-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
 <span data-ttu-id="cb10d-106">Ta funkcja przyjmuje zestaw parametrów, zezwalających na hoście wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="cb10d-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
-   <span data-ttu-id="cb10d-107">Określ wersję środowiska uruchomieniowego, który zostanie załadowany.</span><span class="sxs-lookup"><span data-stu-id="cb10d-107">Specify the version of the runtime that will be loaded.</span></span>  
  
-   <span data-ttu-id="cb10d-108">Wskazuje, czy można załadować kompilacji serwera lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="cb10d-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
-   <span data-ttu-id="cb10d-109">Kontroluje, czy jest wykonywane współbieżne odzyskiwanie pamięci lub z systemem innym niż współbieżnego wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="cb10d-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb10d-110">Współbieżne odzyskiwanie pamięci nie jest obsługiwany w aplikacji uruchomionych WOW64 x86 emulator na 64-bitowe systemy, które implementują architektura Intel Itanium (nazywanych IA-64).</span><span class="sxs-lookup"><span data-stu-id="cb10d-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="cb10d-111">Aby uzyskać więcej informacji o używaniu WOW64 na 64-bitowym systemie Windows, temacie [uruchomiona 32-bitowych aplikacji](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="cb10d-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
-   <span data-ttu-id="cb10d-112">Kontroluje, czy zestawy są ładowane jako neutralne dla domen.</span><span class="sxs-lookup"><span data-stu-id="cb10d-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
-   <span data-ttu-id="cb10d-113">Uzyskiwanie wskaźnika interfejsu do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) można ustawić dodatkowe opcje dotyczące konfigurowania wystąpienia środowiska CLR, przed jego uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="cb10d-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb10d-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb10d-114">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="cb10d-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb10d-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="cb10d-116">[in] Ciąg opisujący wersję środowiska CLR chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="cb10d-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="cb10d-117">Numer wersji w programie .NET Framework składa się z czterech części oddzielone kropkami: *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="cb10d-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="cb10d-118">Ciąg przekazany jako `pwszVersion` musi rozpoczynać się od znaku "v" następuje pierwsze trzy części numer wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="cb10d-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="cb10d-119">Niektóre wersje środowiska CLR są instalowane z instrukcji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="cb10d-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="cb10d-120">Domyślnie, ocenia podkładki uruchamiania `pwszVersion` przed deklaracji zasad i obciążeń najnowszą wersję środowiska uruchomieniowego który jest zgodny z wersją żądanej.</span><span class="sxs-lookup"><span data-stu-id="cb10d-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="cb10d-121">Hosta można wymusić podkładki, aby pominąć oceny zasad i załadować dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości `STARTUP_LOADER_SAFEMODE` dla `startupFlags` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="cb10d-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="cb10d-122">Jeśli element wywołujący określa wartość null dla `pwszVersion`, `CorBindToRuntimeEx` identyfikuje zestaw zainstalowanych środowisk uruchomieniowych których numery wersji są niższe niż środowiska uruchomieniowego .NET Framework 4 i ładuje najnowszą wersję środowiska uruchomieniowego z tego zbioru.</span><span class="sxs-lookup"><span data-stu-id="cb10d-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="cb10d-123">Go nie można załadować programu .NET Framework 4 lub nowszy, a kończy się niepowodzeniem po zainstalowaniu nie starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="cb10d-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="cb10d-124">Należy pamiętać, że przekazywanie null daje hosta bez kontroli, w którym jest załadowana wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cb10d-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="cb10d-125">Chociaż w niektórych scenariuszach może być to rozwiązanie, zaleca się że host podać do ładowania określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="cb10d-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="cb10d-126">[in] Ciąg, który określa, czy ładowanie serwera lub stacji roboczej kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="cb10d-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="cb10d-127">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="cb10d-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="cb10d-128">Zoptymalizowano kompilacji serwera mógł korzystać z wielu procesorów do wyrzucania i kompilacji stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich działających na maszynie jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="cb10d-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="cb10d-129">Jeśli `pwszBuildFlavor` ma wartość null, jest ładowany kompilacji stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="cb10d-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="cb10d-130">Podczas uruchamiania na maszynie jeden procesor, zawsze jest ładowany kompilacji stacji roboczej, nawet jeśli `pwszBuildFlavor` ma ustawioną wartość `svr`.</span><span class="sxs-lookup"><span data-stu-id="cb10d-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="cb10d-131">Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i określono współbieżne odzyskiwanie pamięci (w opisie `startupFlags` parametru), serwer kompilacji został załadowany.</span><span class="sxs-lookup"><span data-stu-id="cb10d-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="cb10d-132">[in] Kombinacja wartości [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb10d-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="cb10d-133">Te flagi kontroli współbieżne odzyskiwanie pamięci, kod o neutralnym poziomie domeny i zachowanie `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="cb10d-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="cb10d-134">Wartość domyślna to jednej domenie, jeśli flaga nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="cb10d-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="cb10d-135">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="cb10d-135">The following values are valid:</span></span>  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="cb10d-136">Aby uzyskać opis tych flag, zobacz [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cb10d-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="cb10d-137">[in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cb10d-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="cb10d-138">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="cb10d-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="cb10d-139">[in] `IID` Żądanego interfejsu z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="cb10d-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="cb10d-140">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="cb10d-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="cb10d-141">[out] Wskaźnik interfejsu zwrócony do `riid`.</span><span class="sxs-lookup"><span data-stu-id="cb10d-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb10d-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb10d-142">Remarks</span></span>  
 <span data-ttu-id="cb10d-143">Jeśli `pwszVersion` Określa wersję środowiska uruchomieniowego, który nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="cb10d-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="cb10d-144">Kontekstu wykonywania i przepływu tożsamości systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cb10d-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="cb10d-145">W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> między punktami asynchronicznego, takie jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza nie przepływ obiektu.</span><span class="sxs-lookup"><span data-stu-id="cb10d-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="cb10d-146">W wersji 2.0 CLR <xref:System.Threading.ExecutionContext> obiekt opakowuje niektóre informacje o obecnie wykonywanym wątku i przepływa go w dowolnym punkcie asynchroniczne, ale nie poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb10d-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="cb10d-147">Podobnie <xref:System.Security.Principal.WindowsIdentity> obiektu przepływa również dla dowolnego punktu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="cb10d-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="cb10d-148">W związku z tym bieżącego personifikacji w wątku, jeśli przepływy zbyt.</span><span class="sxs-lookup"><span data-stu-id="cb10d-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="cb10d-149">Można zmienić przepływu na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="cb10d-149">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="cb10d-150">Zmieniając <xref:System.Threading.ExecutionContext> ustawienia, aby pominąć przepływem na podstawie dla każdego wątku (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="cb10d-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="cb10d-151">Zmieniając to tryb domyślny proces do trybu zgodności wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu dla dowolnego punktu asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="cb10d-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="cb10d-152">Jak zmienić domyślny tryb, zależy od tego, przy użyciu zarządzanego pliku wykonywalnego lub niezarządzane interfejs hostingu można załadować środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="cb10d-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="cb10d-153">Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="cb10d-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="cb10d-154">Niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` oflagowane w `startupFlags` parametr podczas wywoływania metody `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="cb10d-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="cb10d-155">Tryb zgodności wersji 1 dotyczy całego procesu i wszystkich domen aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="cb10d-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb10d-156">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb10d-156">Requirements</span></span>  
 <span data-ttu-id="cb10d-157">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb10d-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb10d-158">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb10d-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb10d-159">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb10d-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb10d-160">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb10d-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb10d-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb10d-161">See Also</span></span>  
 [<span data-ttu-id="cb10d-162">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="cb10d-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="cb10d-163">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="cb10d-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="cb10d-164">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="cb10d-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="cb10d-165">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="cb10d-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="cb10d-166">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb10d-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="cb10d-167">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="cb10d-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
