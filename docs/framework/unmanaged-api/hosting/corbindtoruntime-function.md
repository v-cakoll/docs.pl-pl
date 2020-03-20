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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176516"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="97a56-102">CorBindToRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="97a56-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="97a56-103">Umożliwia hostów niezarządzanych załadować środowiska uruchomieniowego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="97a56-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="97a56-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="97a56-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97a56-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="97a56-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97a56-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97a56-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="97a56-107">[w] Ciąg opisujący wersję clr, który chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="97a56-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="97a56-108">Numer wersji w ramach .NET Framework składa się z czterech części oddzielonych kropkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="97a56-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="97a56-109">Ciąg przeszedł `pwszVersion` zgodnie z musi zaczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="97a56-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="97a56-110">Niektóre wersje programu CLR są instalowane z instrukcją zasad określającą zgodność z poprzednimi wersjami programu CLR.</span><span class="sxs-lookup"><span data-stu-id="97a56-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="97a56-111">Domyślnie podkładka uruchamiania `pwszVersion` ocenia instrukcje zasad i ładuje najnowszą wersję środowiska wykonawczego, która jest zgodna z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="97a56-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="97a56-112">Host może wymusić podkładkę do pominięcia oceny zasad `pwszVersion` i załadować `STARTUP_LOADER_SAFEMODE` dokładną wersję określoną przez przekazanie wartości parametru, `flags` jak opisano poniżej.</span><span class="sxs-lookup"><span data-stu-id="97a56-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="97a56-113">Jeśli wywołujący określa wartość `pwszVersion`null dla , jest ładowana najnowsza wersja środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="97a56-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="97a56-114">Przekazywanie null daje hostowi nie kontrolę nad tym, która wersja środowiska wykonawczego jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="97a56-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="97a56-115">Chociaż takie podejście może być odpowiednie w niektórych scenariuszach, zdecydowanie zaleca się, aby host dostarczał określoną wersję do załadowania.</span><span class="sxs-lookup"><span data-stu-id="97a56-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="97a56-116">[w] Ciąg, który określa, czy załadować serwer lub kompilacji stacji roboczej CLR.</span><span class="sxs-lookup"><span data-stu-id="97a56-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="97a56-117">Prawidłowe `svr` wartości `wks`są i .</span><span class="sxs-lookup"><span data-stu-id="97a56-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="97a56-118">Kompilacja serwera jest zoptymalizowana pod kątem korzystania z wielu procesorów do wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.</span><span class="sxs-lookup"><span data-stu-id="97a56-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="97a56-119">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="97a56-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="97a56-120">Podczas pracy na komputerze z jednym procesorem kompilacja stacji `pwszBuildFlavor` roboczej `svr`jest zawsze ładowana, nawet jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="97a56-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="97a56-121">Jednak jeśli `pwszBuildFlavor` jest `svr` ustawiona i równoczesnych wyrzucania elementów `flags` bezużytecznych jest określony (zobacz opis parametru), kompilacja serwera jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="97a56-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="97a56-122">[w] Coclass, `CLSID` który implementuje interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="97a56-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="97a56-123">Obsługiwane wartości są CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="97a56-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="97a56-124">[w] Wymagany `IID` interfejs z . `rclsid`</span><span class="sxs-lookup"><span data-stu-id="97a56-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="97a56-125">Obsługiwane wartości są IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="97a56-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="97a56-126">[na zewnątrz] Zwrócony wskaźnik `riid`interfejsu do .</span><span class="sxs-lookup"><span data-stu-id="97a56-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97a56-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97a56-127">Remarks</span></span>  
 <span data-ttu-id="97a56-128">Jeśli `pwszVersion` określa wersję środowiska uruchomieniowego, `CorBindToRuntimeEx` która nie istnieje, zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="97a56-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="97a56-129">Kontekst wykonywania i przepływ tożsamości systemu Windows</span><span class="sxs-lookup"><span data-stu-id="97a56-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="97a56-130">W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> obiekt nie przepływa przez punkty asynchroniczne, takie jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza.</span><span class="sxs-lookup"><span data-stu-id="97a56-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="97a56-131">W wersji 2.0 środowiska CLR obiekt zawija <xref:System.Threading.ExecutionContext> niektóre informacje o aktualnie wykonywanym wątku i przepływa przez dowolny punkt asynchroniczne, ale nie przez granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="97a56-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="97a56-132">Podobnie obiekt <xref:System.Security.Principal.WindowsIdentity> przepływa również przez dowolny punkt asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="97a56-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="97a56-133">W związku z tym bieżącej personifikacji w wątku, jeśli istnieje, przepływa zbyt.</span><span class="sxs-lookup"><span data-stu-id="97a56-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="97a56-134">Przepływ można zmienić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="97a56-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="97a56-135">Modyfikując <xref:System.Threading.ExecutionContext> ustawienia w celu wygaszenia przepływu <xref:System.Threading.ExecutionContext.SuppressFlow%2A>na <xref:System.Security.SecurityContext.SuppressFlow%2A>podstawie <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> wątku (patrz , i metody).</span><span class="sxs-lookup"><span data-stu-id="97a56-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="97a56-136">Zmieniając domyślny tryb procesu na tryb zgodności w wersji <xref:System.Security.Principal.WindowsIdentity> 1, w którym obiekt nie przepływa przez <xref:System.Threading.ExecutionContext> żaden punkt asynchroniczne, niezależnie od ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="97a56-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="97a56-137">Sposób zmiany trybu domyślnego zależy od tego, czy do załadowania programu CLR używasz zarządzanego pliku wykonywalnego, czy niezarządzanego interfejsu hostingu:</span><span class="sxs-lookup"><span data-stu-id="97a56-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="97a56-138">W przypadku zarządzanych plików wykonywalnych należy ustawić `enabled` atrybut [ \<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element na `true`.</span><span class="sxs-lookup"><span data-stu-id="97a56-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="97a56-139">W przypadku niezarządzanych interfejsów hostingu ustaw flagę `STARTUP_LEGACY_IMPERSONATION` w parametrze `flags` podczas wywoływania `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="97a56-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="97a56-140">Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i do wszystkich domen aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="97a56-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97a56-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97a56-141">Remarks</span></span>  
 <span data-ttu-id="97a56-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` i wykonać tę samą operację, ale `CorBindToRuntimeEx` funkcja umożliwia ustawienie flagi, aby określić zachowanie CLR.</span><span class="sxs-lookup"><span data-stu-id="97a56-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97a56-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97a56-143">Requirements</span></span>  
 <span data-ttu-id="97a56-144">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97a56-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97a56-145">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97a56-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97a56-146">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="97a56-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97a56-147">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97a56-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a56-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97a56-148">See also</span></span>

- [<span data-ttu-id="97a56-149">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="97a56-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="97a56-150">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="97a56-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="97a56-151">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="97a56-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="97a56-152">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="97a56-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="97a56-153">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="97a56-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="97a56-154">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="97a56-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
