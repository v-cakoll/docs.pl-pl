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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3d714e83eb0b75b31b08e7a356eb9ea699e1794
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689198"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="8622f-102">CorBindToRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="8622f-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="8622f-103">Włącza niezarządzane hosty do załadowania środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="8622f-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="8622f-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8622f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8622f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8622f-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8622f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8622f-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="8622f-107">[in] Ciąg opisujący wersję środowiska CLR chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="8622f-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="8622f-108">Numer wersji w programie .NET Framework składa się z czterech części oddzielonych kropkami: *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="8622f-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="8622f-109">Ciąg przekazany jako `pwszVersion` musi zaczynać się od znaków "v", następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="8622f-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="8622f-110">Niektóre wersje środowiska CLR są instalowane z deklaracji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8622f-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="8622f-111">Domyślnie, uruchomienie podkładki programowej ocenia `pwszVersion` wobec deklaracji i obciążeń najnowszej wersji środowiska uruchomieniowego, jest zgodny z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="8622f-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="8622f-112">Host może wymusić podkładkę, aby pominąć zasady oceny i załadować dokładną wersję określoną w `pwszVersion` , przekazując wartość `STARTUP_LOADER_SAFEMODE` dla `flags` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="8622f-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="8622f-113">Jeśli obiekt wywołujący określa wartość null w przypadku `pwszVersion`, najnowszą wersję środowiska wykonawczego jest załadowana.</span><span class="sxs-lookup"><span data-stu-id="8622f-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="8622f-114">Przekazanie wartości null zapewnia hosta bez kontroli nad tym, którzy wersja środowiska uruchomieniowego jest załadowana.</span><span class="sxs-lookup"><span data-stu-id="8622f-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="8622f-115">Mimo że takie podejście może być odpowiedni w niektórych scenariuszach, zdecydowanie zaleca się że host podać do załadowania określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="8622f-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="8622f-116">[in] Ciąg, który określa, czy ładować serwer czy stację roboczą kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8622f-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="8622f-117">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="8622f-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="8622f-118">Server kompilacji jest zoptymalizowany, aby móc korzystać z wielu procesorów do wyrzucania elementów bezużytecznych, a stacja robocza kompilacji jest zoptymalizowany dla aplikacji klienckich działających na komputerze jednoprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="8622f-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="8622f-119">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, stacja robocza kompilacji jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="8622f-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="8622f-120">Podczas uruchamiania na komputerze jednoprocesorowym, stacja robocza kompilacji będzie zawsze ładowana, nawet jeśli `pwszBuildFlavor` ustawiono `svr`.</span><span class="sxs-lookup"><span data-stu-id="8622f-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="8622f-121">Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i współbieżne wyrzucanie elementów bezużytecznych zostało określone (zobacz opis `flags` parametru), ładowana jest kompilacja serwera.</span><span class="sxs-lookup"><span data-stu-id="8622f-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="8622f-122">[in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8622f-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="8622f-123">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="8622f-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="8622f-124">[in] `IID` Żądanego interfejsu z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="8622f-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="8622f-125">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="8622f-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="8622f-126">[out] Wskaźnik interfejsu zwrócone do `riid`.</span><span class="sxs-lookup"><span data-stu-id="8622f-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8622f-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8622f-127">Remarks</span></span>  
 <span data-ttu-id="8622f-128">Jeśli `pwszVersion` Określa wersję środowiska uruchomieniowego, który nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="8622f-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="8622f-129">Kontekstu wykonywania i przepływ tożsamości Windows</span><span class="sxs-lookup"><span data-stu-id="8622f-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="8622f-130">W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> obiektu nie przepływać przez punkty asynchroniczne, takie jak nowe wątki, pul wątków lub czasomierza wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="8622f-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="8622f-131">W wersji 2.0 środowisko CLR <xref:System.Threading.ExecutionContext> obiektu otacza pewne informacje o aktualnie wykonywany wątek i przepływy go między kiedykolwiek asynchronicznego, ale nie granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8622f-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="8622f-132">Podobnie <xref:System.Security.Principal.WindowsIdentity> obiektu również odbywa się za pośrednictwem dowolnego punktu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="8622f-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="8622f-133">W związku z tym bieżący personifikacji w wątku, ewentualnie przepływów zbyt.</span><span class="sxs-lookup"><span data-stu-id="8622f-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="8622f-134">Można zmienić przepływ na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="8622f-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="8622f-135">Modyfikując <xref:System.Threading.ExecutionContext> ustawienia, aby wstrzymać przepływ na podstawie na wątek (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="8622f-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="8622f-136">Po zmianie procesu domyślny tryb na tryb zgodności w wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu w dowolnym momencie asynchronicznego niezależnie od wartości <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="8622f-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="8622f-137">Jak zmienić domyślny tryb, zależy od tego, czy używać zarządzanego pliku wykonywalnego lub niezarządzanego interfejsu hostingu do ładowania CLR:</span><span class="sxs-lookup"><span data-stu-id="8622f-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="8622f-138">Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="8622f-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="8622f-139">W przypadku niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` znacznik w `flags` parametru podczas wywoływania `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="8622f-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="8622f-140">Tryb zgodności w wersji 1 ma zastosowanie do całego procesu i wszystkie domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="8622f-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8622f-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8622f-141">Remarks</span></span>  
 <span data-ttu-id="8622f-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i `CorBindToRuntime` wykonanie tej samej operacji, ale `CorBindToRuntimeEx` funkcja pozwala na ustawienie flagi, aby określić zachowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8622f-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8622f-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8622f-143">Requirements</span></span>  
 <span data-ttu-id="8622f-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8622f-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8622f-145">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8622f-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8622f-146">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8622f-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8622f-147">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8622f-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8622f-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8622f-148">See also</span></span>
- [<span data-ttu-id="8622f-149">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="8622f-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="8622f-150">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="8622f-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="8622f-151">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="8622f-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="8622f-152">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="8622f-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="8622f-153">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="8622f-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="8622f-154">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="8622f-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
