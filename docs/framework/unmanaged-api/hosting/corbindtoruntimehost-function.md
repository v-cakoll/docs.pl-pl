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
ms.openlocfilehash: 1952121a6c0c735926944c839c3c7e8a8db5fb53
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723197"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="a8311-102">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a8311-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="a8311-103">Włącza hosty do załadowania określonej wersji środowiska uruchomieniowego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="a8311-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="a8311-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8311-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8311-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8311-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a8311-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8311-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="a8311-107">[in] Ciąg, który opisuje wersję środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="a8311-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="a8311-108">Numer wersji w programie .NET Framework składa się z czterech części oddzielonych kropkami: *główna.pomocnicza.kompilacja.poprawka*.</span><span class="sxs-lookup"><span data-stu-id="a8311-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="a8311-109">Ciąg przekazany jako `pwszVersion` musi zaczynać się od znaków "v", następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="a8311-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="a8311-110">Niektóre wersje środowiska CLR są instalowane z deklaracji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a8311-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="a8311-111">Domyślnie, uruchomienie podkładki programowej ocenia `pwszVersion` wobec deklaracji i obciążeń najnowszej wersji środowiska uruchomieniowego, jest zgodny z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="a8311-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="a8311-112">Host może wymusić podkładkę, aby pominąć zasady oceny i załadować dokładną wersję określoną w `pwszVersion` , przekazując wartość STARTUP_LOADER_SAFEMODE dla `startupFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8311-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="a8311-113">Jeśli `pwszVersion` jest `null,` metoda nie ładuje żadnych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a8311-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="a8311-114">Zamiast tego zwraca CLR_E_SHIM_RUNTIMELOAD, co oznacza, że nie można załadować środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="a8311-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="a8311-115">[in] Ciąg, który określa, czy ładować serwer czy stację roboczą kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a8311-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="a8311-116">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="a8311-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="a8311-117">Server kompilacji jest zoptymalizowany, aby móc korzystać z wielu procesorów do wyrzucania elementów bezużytecznych, a stacja robocza kompilacji jest zoptymalizowany dla aplikacji klienckich działających na komputerze jednoprocesorowym.</span><span class="sxs-lookup"><span data-stu-id="a8311-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="a8311-118">Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, stacja robocza kompilacji jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="a8311-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="a8311-119">Podczas uruchamiania na komputerze jednoprocesorowym, stacja robocza kompilacji będzie zawsze ładowana, nawet jeśli `pwszBuildFlavor` ustawiono `svr`.</span><span class="sxs-lookup"><span data-stu-id="a8311-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="a8311-120">Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i współbieżne wyrzucanie elementów bezużytecznych zostało określone (zobacz opis `startupFlags` parametru), ładowana jest kompilacja serwera.</span><span class="sxs-lookup"><span data-stu-id="a8311-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8311-121">Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwana w aplikacjach działających w emulatorze WOW64 x86 emulatora w systemach 64-bitowych, które implementują architekturę Intel Itanium (wcześniej noszącą nazwę IA-64).</span><span class="sxs-lookup"><span data-stu-id="a8311-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="a8311-122">Aby uzyskać więcej informacji o używaniu WOW64 w 64-bitowych systemach Windows, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="a8311-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="a8311-123">[in] Nazwa pliku konfiguracyjnego hosta, który określa wersja środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="a8311-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="a8311-124">Jeśli nazwa pliku zawiera pełną ścieżkę, plik zakłada się, że w tym samym katalogu co plik wykonywalny, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="a8311-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="a8311-125">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="a8311-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a8311-126">[in] Zestaw flag, które kontroluje współbieżne wyrzucanie elementów bezużytecznych, kodem domeny neutralnej i zachowaniem `pwszVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8311-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="a8311-127">Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a8311-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="a8311-128">Aby uzyskać listę obsługiwanych wartości, zobacz [startup_flags — wyliczenie](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a8311-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a8311-129">[in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a8311-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a8311-130">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a8311-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a8311-131">[in] `IID` Dla żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a8311-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="a8311-132">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a8311-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a8311-133">[out] Wskaźnik interfejsu do wersji środowiska uruchomieniowego, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="a8311-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8311-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8311-134">Requirements</span></span>  
 <span data-ttu-id="a8311-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8311-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8311-136">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="a8311-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a8311-137">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8311-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8311-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8311-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8311-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8311-139">See Also</span></span>  
 [<span data-ttu-id="a8311-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="a8311-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="a8311-141">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="a8311-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="a8311-142">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="a8311-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="a8311-143">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="a8311-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="a8311-144">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8311-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="a8311-145">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a8311-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
