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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176490"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="930a6-102">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="930a6-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="930a6-103">Umożliwia hostom załadowanie określonej wersji środowiska wykonawczego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="930a6-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="930a6-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="930a6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="930a6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="930a6-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="930a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="930a6-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="930a6-107">[w] Ciąg opisujący wersję programu CLR, którą chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="930a6-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="930a6-108">Numer wersji w ramach .NET Framework składa się z czterech części oddzielonych kropkami: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="930a6-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="930a6-109">Ciąg przeszedł `pwszVersion` zgodnie z musi zaczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="930a6-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="930a6-110">Niektóre wersje programu CLR są instalowane z instrukcją zasad określającą zgodność z poprzednimi wersjami programu CLR.</span><span class="sxs-lookup"><span data-stu-id="930a6-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="930a6-111">Domyślnie podkładka uruchamiania `pwszVersion` ocenia instrukcje zasad i ładuje najnowszą wersję środowiska wykonawczego, która jest zgodna z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="930a6-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="930a6-112">Host może wymusić podkładkę, aby pominąć oceny `pwszVersion` zasad i załadować dokładną wersję `startupFlags` określoną w przekazując wartość STARTUP_LOADER_SAFEMODE dla parametru.</span><span class="sxs-lookup"><span data-stu-id="930a6-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="930a6-113">Jeśli `pwszVersion` `null,` jest metoda nie ładuje żadnej wersji CLR.</span><span class="sxs-lookup"><span data-stu-id="930a6-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="930a6-114">Zamiast tego zwraca CLR_E_SHIM_RUNTIMELOAD, co wskazuje, że nie można załadować środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="930a6-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="930a6-115">[w] Ciąg, który określa, czy załadować serwer lub kompilacji stacji roboczej CLR.</span><span class="sxs-lookup"><span data-stu-id="930a6-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="930a6-116">Prawidłowe `svr` wartości `wks`są i .</span><span class="sxs-lookup"><span data-stu-id="930a6-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="930a6-117">Kompilacja serwera jest zoptymalizowana pod kątem korzystania z wielu procesorów do wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.</span><span class="sxs-lookup"><span data-stu-id="930a6-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="930a6-118">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej jest ładowana.</span><span class="sxs-lookup"><span data-stu-id="930a6-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="930a6-119">Podczas pracy na komputerze z jednym procesorem kompilacja stacji `pwszBuildFlavor` roboczej `svr`jest zawsze ładowana, nawet jeśli jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="930a6-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="930a6-120">Jednak jeśli `pwszBuildFlavor` jest `svr` ustawiona i równoczesnych wyrzucania elementów `startupFlags` bezużytecznych jest określony (zobacz opis parametru), kompilacja serwera jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="930a6-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="930a6-121">Równoczesne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach z emulatorem WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej nazywaną IA-64).</span><span class="sxs-lookup"><span data-stu-id="930a6-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="930a6-122">Aby uzyskać więcej informacji na temat używania WOW64 w 64-bitowych systemach Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="930a6-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="930a6-123">[w] Nazwa pliku konfiguracji hosta, który określa wersję clr do załadowania.</span><span class="sxs-lookup"><span data-stu-id="930a6-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="930a6-124">Jeśli nazwa pliku nie zawiera w pełni kwalifikowanej ścieżki, zakłada się, że plik znajduje się w tym samym katalogu co plik wykonywalny, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="930a6-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="930a6-125">[w] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="930a6-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="930a6-126">[w] Zestaw flag, który kontroluje równoczesnych wyrzucania elementów bezużytecznych, `pwszVersion` kod neutralny dla domeny i zachowanie parametru.</span><span class="sxs-lookup"><span data-stu-id="930a6-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="930a6-127">Wartość domyślna to pojedyncza domena, jeśli nie ustawiono żadnej flagi.</span><span class="sxs-lookup"><span data-stu-id="930a6-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="930a6-128">Aby uzyskać listę obsługiwanych wartości, zobacz [STARTUP_FLAGS wyliczenie](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="930a6-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="930a6-129">[w] Coclass, `CLSID` który implementuje interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="930a6-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="930a6-130">Obsługiwane wartości są CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="930a6-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="930a6-131">[w] Interfejs, `IID` o który prosisz.</span><span class="sxs-lookup"><span data-stu-id="930a6-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="930a6-132">Obsługiwane wartości są IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="930a6-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="930a6-133">[na zewnątrz] Wskaźnik interfejsu do wersji środowiska wykonawczego, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="930a6-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="930a6-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="930a6-134">Requirements</span></span>  
 <span data-ttu-id="930a6-135">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="930a6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="930a6-136">**Nagłówek:** mscoree.idl</span><span class="sxs-lookup"><span data-stu-id="930a6-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="930a6-137">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="930a6-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="930a6-138">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="930a6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930a6-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="930a6-139">See also</span></span>

- [<span data-ttu-id="930a6-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="930a6-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="930a6-141">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="930a6-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="930a6-142">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="930a6-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="930a6-143">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="930a6-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="930a6-144">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="930a6-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="930a6-145">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="930a6-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
