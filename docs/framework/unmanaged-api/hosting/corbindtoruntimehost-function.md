---
title: CorBindToRuntimeHost — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c1d83b32402343f3cd2b5403e328698abd6a930
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="f4592-102">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f4592-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="f4592-103">Umożliwia hostom do ładowania określonej wersji środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="f4592-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="f4592-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4592-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4592-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4592-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4592-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4592-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="f4592-107">[in] Ciąg opisujący wersję środowiska CLR chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="f4592-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="f4592-108">Numer wersji w programie .NET Framework składa się z czterech części oddzielone kropkami: *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="f4592-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="f4592-109">Ciąg przekazany jako `pwszVersion` musi rozpoczynać się od znaku "v" następuje pierwsze trzy części numer wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="f4592-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="f4592-110">Niektóre wersje środowiska CLR są instalowane z instrukcji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f4592-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="f4592-111">Domyślnie, ocenia podkładki uruchamiania `pwszVersion` przed deklaracji zasad i obciążeń najnowszą wersję środowiska uruchomieniowego który jest zgodny z wersją żądanej.</span><span class="sxs-lookup"><span data-stu-id="f4592-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="f4592-112">Hosta można wymusić podkładki, aby pominąć oceny zasad i załadować dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości STARTUP_LOADER_SAFEMODE dla `startupFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="f4592-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="f4592-113">Jeśli `pwszVersion` jest `null,` metody nie zostanie załadowany z dowolnej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f4592-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="f4592-114">W zamian zwraca CLR_E_SHIM_RUNTIMELOAD, co oznacza, że nie można załadować środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="f4592-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="f4592-115">[in] Ciąg, który określa, czy ładowanie serwera lub stacji roboczej kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f4592-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="f4592-116">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="f4592-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="f4592-117">Zoptymalizowano kompilacji serwera mógł korzystać z wielu procesorów do wyrzucania i kompilacji stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich działających na maszynie jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="f4592-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="f4592-118">Jeśli `pwszBuildFlavor` ma wartość null, jest ładowany kompilacji stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="f4592-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="f4592-119">Podczas uruchamiania na maszynie jeden procesor, zawsze jest ładowany kompilacji stacji roboczej, nawet jeśli `pwszBuildFlavor` ma ustawioną wartość `svr`.</span><span class="sxs-lookup"><span data-stu-id="f4592-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="f4592-120">Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i określono współbieżne odzyskiwanie pamięci (w opisie `startupFlags` parametru), serwer kompilacji został załadowany.</span><span class="sxs-lookup"><span data-stu-id="f4592-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4592-121">Współbieżne odzyskiwanie pamięci nie jest obsługiwany w aplikacji uruchomionych WOW64 x86 emulator na 64-bitowe systemy, które implementują architektura Intel Itanium (nazywanych IA-64).</span><span class="sxs-lookup"><span data-stu-id="f4592-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="f4592-122">Aby uzyskać więcej informacji o używaniu WOW64 na 64-bitowym systemie Windows, temacie [uruchomiona 32-bitowych aplikacji](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="f4592-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="f4592-123">[in] Nazwa pliku konfiguracji hosta, który określa wersję środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="f4592-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="f4592-124">Jeśli nazwa pliku nie ma w pełni kwalifikowana, plik zakłada się, że w tym samym katalogu co plik wykonywalny, który jest wywołania.</span><span class="sxs-lookup"><span data-stu-id="f4592-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="f4592-125">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="f4592-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="f4592-126">[in] Zestaw flag, które kontroluje współbieżne odzyskiwanie pamięci, kod o neutralnym poziomie domeny i zachowanie `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="f4592-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="f4592-127">Wartość domyślna to jednej domenie, jeśli flaga nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="f4592-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="f4592-128">Aby uzyskać listę obsługiwanych wartości, zobacz [STARTUP_FLAGS — wyliczenie](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f4592-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="f4592-129">[in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f4592-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="f4592-130">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f4592-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="f4592-131">[in] `IID` Interfejsu żądania dostępu.</span><span class="sxs-lookup"><span data-stu-id="f4592-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="f4592-132">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f4592-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f4592-133">[out] Wskaźnik interfejsu do wersji środowiska uruchomieniowego, które zostały załadowane.</span><span class="sxs-lookup"><span data-stu-id="f4592-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4592-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4592-134">Requirements</span></span>  
 <span data-ttu-id="f4592-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4592-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4592-136">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="f4592-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f4592-137">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4592-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4592-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4592-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4592-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4592-139">See Also</span></span>  
 [<span data-ttu-id="f4592-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="f4592-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="f4592-141">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="f4592-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="f4592-142">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="f4592-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="f4592-143">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="f4592-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="f4592-144">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4592-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="f4592-145">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="f4592-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
