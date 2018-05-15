---
title: GetRequestedRuntimeInfo — Funkcja
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f37be8e3d2e92147e9f13954ab64396062ade2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="ff70a-102">GetRequestedRuntimeInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ff70a-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="ff70a-103">Pobiera informacje o wersji i katalogu o środowisko uruchomieniowe języka wspólnego (CLR) wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ff70a-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="ff70a-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff70a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff70a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff70a-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff70a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff70a-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="ff70a-107">[in] Nazwa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ff70a-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="ff70a-108">[in] Ciąg określający numer wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ff70a-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="ff70a-109">[in] Nazwa pliku konfiguracji, który jest skojarzony z `pExe`.</span><span class="sxs-lookup"><span data-stu-id="ff70a-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="ff70a-110">[in] Co najmniej jednego [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ff70a-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="ff70a-111">[in] Co najmniej jednego [runtime_info_flags —](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ff70a-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="ff70a-112">[out] Buforu, który zawiera ścieżkę katalogu do środowiska wykonawczego po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="ff70a-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="ff70a-113">[in] Długość buforu katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff70a-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="ff70a-114">[out] Wskaźnik do długości ciągu ścieżki katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff70a-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ff70a-115">[out] Buforu, który zawiera numer wersji środowiska uruchomieniowego na pomyślne zakończenie.</span><span class="sxs-lookup"><span data-stu-id="ff70a-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ff70a-116">[in] Długość buforu ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="ff70a-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="ff70a-117">[out] Wskaźnik do długości ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="ff70a-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff70a-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ff70a-118">Return Value</span></span>  
 <span data-ttu-id="ff70a-119">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="ff70a-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ff70a-120">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="ff70a-120">Return code</span></span>|<span data-ttu-id="ff70a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ff70a-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ff70a-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff70a-122">S_OK</span></span>|<span data-ttu-id="ff70a-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ff70a-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="ff70a-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ff70a-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ff70a-125">Bufor katalogu nie jest wystarczająco duży, aby przechowywać ścieżki katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff70a-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="ff70a-126">- lub -</span><span class="sxs-lookup"><span data-stu-id="ff70a-126">- or -</span></span><br /><br /> <span data-ttu-id="ff70a-127">Bufor wersji nie jest wystarczająco duży, aby zapisać ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="ff70a-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff70a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff70a-128">Remarks</span></span>  
 <span data-ttu-id="ff70a-129">`GetRequestedRuntimeInfo` Metoda zwraca wartość czasu wykonywania informacji o wersji załadowany do procesu, który nie musi być najnowszą wersję zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ff70a-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="ff70a-130">Informacje o najnowszej wersji zainstalowanej w programie .NET Framework w wersji 2.0, można uzyskać za pomocą `GetRequestedRuntimeInfo` metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ff70a-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
-   <span data-ttu-id="ff70a-131">Określ `pExe`, `pwszVersion`, i `pConfigurationFile` parametrów jako wartość null.</span><span class="sxs-lookup"><span data-stu-id="ff70a-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
-   <span data-ttu-id="ff70a-132">Określ flagę RUNTIME_INFO_UPGRADE_VERSION `RUNTIME_INFO_FLAGS` wyliczenia dla `runtimeInfoFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="ff70a-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="ff70a-133">`GetRequestedRuntimeInfo` Metoda nie zwraca najnowszą wersję środowiska CLR w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="ff70a-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
-   <span data-ttu-id="ff70a-134">Istnieje plik konfiguracji aplikacji, która określa ładowania określonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ff70a-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="ff70a-135">Należy pamiętać, że programu .NET Framework będzie pliku konfiguracji nawet, jeśli określono wartość null dla `pConfigurationFile` parametru.</span><span class="sxs-lookup"><span data-stu-id="ff70a-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
-   <span data-ttu-id="ff70a-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) wywołano metodę określania starszej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ff70a-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
-   <span data-ttu-id="ff70a-137">Obecnie jest uruchomiona aplikacja, która została skompilowana dla starszej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ff70a-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="ff70a-138">Dla `runtimeInfoFlags` parametru, można określić tylko jeden stałe architektura `RUNTIME_INFO_FLAGS` wyliczenie jednocześnie:</span><span class="sxs-lookup"><span data-stu-id="ff70a-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
-   <span data-ttu-id="ff70a-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="ff70a-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="ff70a-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="ff70a-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="ff70a-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="ff70a-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff70a-142">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff70a-142">Requirements</span></span>  
 <span data-ttu-id="ff70a-143">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff70a-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff70a-144">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff70a-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff70a-145">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff70a-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff70a-146">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff70a-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff70a-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff70a-147">See Also</span></span>  
 [<span data-ttu-id="ff70a-148">GetRequestedRuntimeVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="ff70a-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="ff70a-149">GetVersionFromProcess, funkcja</span><span class="sxs-lookup"><span data-stu-id="ff70a-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="ff70a-150">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="ff70a-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
