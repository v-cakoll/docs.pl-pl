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
ms.openlocfilehash: a6d9708e7281a72c88ba28012006784f7b0ee9d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124357"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="0b112-102">CorBindToRuntimeHost — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0b112-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="0b112-103">Włącza hosty do załadowania określonej wersji środowiska uruchomieniowego języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="0b112-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="0b112-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0b112-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b112-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b112-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0b112-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b112-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="0b112-107">podczas Ciąg opisujący wersję środowiska CLR, które chcesz załadować.</span><span class="sxs-lookup"><span data-stu-id="0b112-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="0b112-108">Numer wersji w .NET Framework składa się z czterech części oddzielonych kropkami: *główna. pomocnicza. kompilacja. poprawka*.</span><span class="sxs-lookup"><span data-stu-id="0b112-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="0b112-109">Ciąg przesłany jako `pwszVersion` musi rozpoczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="0b112-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="0b112-110">Niektóre wersje środowiska CLR są instalowane z instrukcją zasad, która określa zgodność z poprzednimi wersjami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0b112-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="0b112-111">Domyślnie podkładka uruchamiania szacuje `pwszVersion` względem instrukcji zasad i ładuje najnowszą wersję środowiska uruchomieniowego, która jest zgodna z żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="0b112-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="0b112-112">Host może zmusić podkładkę do pominięcia oceny zasad i załadowania dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości STARTUP_LOADER_SAFEMODE dla parametru `startupFlags`.</span><span class="sxs-lookup"><span data-stu-id="0b112-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="0b112-113">Jeśli `pwszVersion` jest `null,` Metoda nie ładuje żadnej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0b112-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="0b112-114">Zamiast tego zwraca CLR_E_SHIM_RUNTIMELOAD, co oznacza, że ładowanie środowiska uruchomieniowego nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0b112-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="0b112-115">podczas Ciąg określający, czy załadować serwer lub kompilację stacji roboczej środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0b112-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="0b112-116">Prawidłowe wartości to `svr` i `wks`.</span><span class="sxs-lookup"><span data-stu-id="0b112-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="0b112-117">Kompilacja serwera jest zoptymalizowana pod kątem wykorzystania wielu procesorów na potrzeby wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.</span><span class="sxs-lookup"><span data-stu-id="0b112-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="0b112-118">Jeśli `pwszBuildFlavor` ma wartość null, zostanie załadowana kompilacja stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="0b112-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="0b112-119">W przypadku uruchamiania na komputerze z jednym procesorem kompilacja stacji roboczej jest zawsze ładowana, nawet jeśli `pwszBuildFlavor` jest ustawiona na `svr`.</span><span class="sxs-lookup"><span data-stu-id="0b112-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="0b112-120">Jeśli jednak `pwszBuildFlavor` jest ustawiona na `svr` i zostanie określone współbieżne wyrzucanie elementów bezużytecznych (zobacz opis parametru `startupFlags`), kompilacja serwera zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="0b112-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b112-121">Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach uruchamiających emulator WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej zwane IA-64).</span><span class="sxs-lookup"><span data-stu-id="0b112-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="0b112-122">Aby uzyskać więcej informacji na temat korzystania z emulatora WOW64 w systemach 64-bitowych systemu Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="0b112-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="0b112-123">podczas Nazwa pliku konfiguracji hosta, który określa wersję środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="0b112-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="0b112-124">Jeśli nazwa pliku nie zawiera w pełni kwalifikowanej ścieżki, zakłada się, że plik znajduje się w tym samym katalogu co plik wykonywalny, który wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="0b112-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="0b112-125">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="0b112-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="0b112-126">podczas Zestaw flag kontrolujących współbieżne odzyskiwanie pamięci, kod neutralny przez domenę i zachowanie parametru `pwszVersion`.</span><span class="sxs-lookup"><span data-stu-id="0b112-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="0b112-127">Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="0b112-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="0b112-128">Aby uzyskać listę obsługiwanych wartości, zobacz [Wyliczenie STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0b112-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0b112-129">podczas `CLSID` klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0b112-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0b112-130">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0b112-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0b112-131">podczas `IID` żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0b112-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="0b112-132">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0b112-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0b112-133">określoną Wskaźnik interfejsu do wersji środowiska uruchomieniowego, która została załadowana.</span><span class="sxs-lookup"><span data-stu-id="0b112-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b112-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b112-134">Requirements</span></span>  
 <span data-ttu-id="0b112-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b112-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b112-136">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="0b112-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0b112-137">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b112-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b112-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b112-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b112-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b112-139">See also</span></span>

- [<span data-ttu-id="0b112-140">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="0b112-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0b112-141">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="0b112-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="0b112-142">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="0b112-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="0b112-143">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="0b112-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="0b112-144">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b112-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="0b112-145">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="0b112-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
