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
ms.openlocfilehash: 36b15c607026ea9ce583ecda02bcb8ac43900310
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435754"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="7e69b-102">CorBindToRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7e69b-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="7e69b-103">Umożliwia niezarządzane hosty załadować środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="7e69b-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="7e69b-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e69b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e69b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e69b-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e69b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e69b-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="7e69b-107">[in] Ciąg opisujący wersję środowiska CLR chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="7e69b-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="7e69b-108">Numer wersji w programie .NET Framework składa się z czterech części oddzielone kropkami: *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="7e69b-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="7e69b-109">Ciąg przekazany jako `pwszVersion` musi rozpoczynać się od znaku "v" następuje pierwsze trzy części numer wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="7e69b-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="7e69b-110">Niektóre wersje środowiska CLR są instalowane z instrukcji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7e69b-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="7e69b-111">Domyślnie, ocenia podkładki uruchamiania `pwszVersion` przed deklaracji zasad i obciążeń najnowszą wersję środowiska uruchomieniowego który jest zgodny z wersją żądanej.</span><span class="sxs-lookup"><span data-stu-id="7e69b-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="7e69b-112">Hosta można wymusić podkładki, aby pominąć oceny zasad i załadować dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości `STARTUP_LOADER_SAFEMODE` dla `flags` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="7e69b-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="7e69b-113">Jeśli element wywołujący określa wartość null dla `pwszVersion`, najnowszą wersję środowiska wykonawczego został załadowany.</span><span class="sxs-lookup"><span data-stu-id="7e69b-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="7e69b-114">Przekazywanie null daje hosta bez kontroli, w którym jest załadowana wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7e69b-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="7e69b-115">Chociaż w niektórych scenariuszach może być to rozwiązanie, zaleca się że host podać do ładowania określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="7e69b-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="7e69b-116">[in] Ciąg, który określa, czy ładowanie serwera lub stacji roboczej kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7e69b-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="7e69b-117">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="7e69b-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="7e69b-118">Zoptymalizowano kompilacji serwera mógł korzystać z wielu procesorów do wyrzucania i kompilacji stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich działających na maszynie jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="7e69b-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="7e69b-119">Jeśli `pwszBuildFlavor` ma wartość null, jest ładowany kompilacji stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="7e69b-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="7e69b-120">Podczas uruchamiania na maszynie jeden procesor, zawsze jest ładowany kompilacji stacji roboczej, nawet jeśli `pwszBuildFlavor` ma ustawioną wartość `svr`.</span><span class="sxs-lookup"><span data-stu-id="7e69b-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="7e69b-121">Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i określono współbieżne odzyskiwanie pamięci (w opisie `flags` parametru), serwer kompilacji został załadowany.</span><span class="sxs-lookup"><span data-stu-id="7e69b-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="7e69b-122">[in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7e69b-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="7e69b-123">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="7e69b-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="7e69b-124">[in] `IID` Żądanego interfejsu z `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="7e69b-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="7e69b-125">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="7e69b-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="7e69b-126">[out] Wskaźnik interfejsu zwrócony do `riid`.</span><span class="sxs-lookup"><span data-stu-id="7e69b-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e69b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e69b-127">Remarks</span></span>  
 <span data-ttu-id="7e69b-128">Jeśli `pwszVersion` Określa wersję środowiska uruchomieniowego, który nie istnieje, `CorBindToRuntimeEx` zwraca wartość HRESULT CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="7e69b-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="7e69b-129">Kontekstu wykonywania i przepływu tożsamości systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7e69b-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="7e69b-130">W wersji 1 CLR <xref:System.Security.Principal.WindowsIdentity> między punktami asynchronicznego, takie jak nowe wątki, pule wątków lub wywołania zwrotne czasomierza nie przepływ obiektu.</span><span class="sxs-lookup"><span data-stu-id="7e69b-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="7e69b-131">W wersji 2.0 CLR <xref:System.Threading.ExecutionContext> obiekt opakowuje niektóre informacje o obecnie wykonywanym wątku i przepływa go w dowolnym punkcie asynchroniczne, ale nie poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e69b-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="7e69b-132">Podobnie <xref:System.Security.Principal.WindowsIdentity> obiektu przepływa również dla dowolnego punktu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="7e69b-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="7e69b-133">W związku z tym bieżącego personifikacji w wątku, jeśli przepływy zbyt.</span><span class="sxs-lookup"><span data-stu-id="7e69b-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="7e69b-134">Można zmienić przepływu na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="7e69b-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="7e69b-135">Zmieniając <xref:System.Threading.ExecutionContext> ustawienia, aby pominąć przepływem na podstawie dla każdego wątku (zobacz <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, i <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).</span><span class="sxs-lookup"><span data-stu-id="7e69b-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="7e69b-136">Zmieniając to tryb domyślny proces do trybu zgodności wersji 1, gdzie <xref:System.Security.Principal.WindowsIdentity> nie przepływ obiektu dla dowolnego punktu asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="7e69b-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="7e69b-137">Jak zmienić domyślny tryb, zależy od tego, przy użyciu zarządzanego pliku wykonywalnego lub niezarządzane interfejs hostingu można załadować środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="7e69b-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="7e69b-138">Dla zarządzanych plików wykonywalnych, należy ustawić `enabled` atrybutu [ \<legacyimpersonationpolicy — >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="7e69b-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="7e69b-139">Niezarządzane interfejsy hostingu, skonfigurować `STARTUP_LEGACY_IMPERSONATION` oflagowane w `flags` parametr podczas wywoływania metody `CorBindToRuntimeEx` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7e69b-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="7e69b-140">Tryb zgodności wersji 1 dotyczy całego procesu i wszystkich domen aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="7e69b-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e69b-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e69b-141">Remarks</span></span>  
 <span data-ttu-id="7e69b-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i `CorBindToRuntime` wykonać operację, ale `CorBindToRuntimeEx` funkcji można ustawić flagi, aby określić zachowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7e69b-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e69b-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e69b-143">Requirements</span></span>  
 <span data-ttu-id="7e69b-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e69b-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e69b-145">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e69b-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e69b-146">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e69b-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e69b-147">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e69b-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e69b-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e69b-148">See Also</span></span>  
 [<span data-ttu-id="7e69b-149">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="7e69b-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="7e69b-150">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="7e69b-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="7e69b-151">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="7e69b-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="7e69b-152">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="7e69b-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="7e69b-153">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e69b-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="7e69b-154">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="7e69b-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
