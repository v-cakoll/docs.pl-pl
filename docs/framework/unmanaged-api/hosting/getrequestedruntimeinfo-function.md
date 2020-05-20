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
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617181"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="7a457-102">GetRequestedRuntimeInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7a457-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="7a457-103">Pobiera informacje o wersji i katalogu dotyczące środowiska uruchomieniowego języka wspólnego (CLR) żądanego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7a457-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="7a457-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7a457-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a457-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a457-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="7a457-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a457-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="7a457-107">podczas Nazwa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a457-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="7a457-108">podczas Ciąg określający numer wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7a457-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="7a457-109">podczas Nazwa pliku konfiguracji, który jest skojarzony z `pExe` .</span><span class="sxs-lookup"><span data-stu-id="7a457-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="7a457-110">podczas Co najmniej jedna [STARTUP_FLAGS](startup-flags-enumeration.md) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7a457-110">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="7a457-111">podczas Co najmniej jedna [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7a457-111">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="7a457-112">określoną Bufor, który zawiera ścieżkę katalogu do środowiska uruchomieniowego po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="7a457-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="7a457-113">podczas Długość buforu katalogów.</span><span class="sxs-lookup"><span data-stu-id="7a457-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="7a457-114">określoną Wskaźnik do długości ciągu ścieżki katalogu.</span><span class="sxs-lookup"><span data-stu-id="7a457-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7a457-115">określoną Bufor zawierający numer wersji środowiska uruchomieniowego po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="7a457-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7a457-116">podczas Długość buforu ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="7a457-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="7a457-117">określoną Wskaźnik do długości ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="7a457-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a457-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a457-118">Return Value</span></span>  
 <span data-ttu-id="7a457-119">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="7a457-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7a457-120">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="7a457-120">Return code</span></span>|<span data-ttu-id="7a457-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7a457-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7a457-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a457-122">S_OK</span></span>|<span data-ttu-id="7a457-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7a457-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="7a457-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7a457-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7a457-125">Bufor katalogów nie jest wystarczająco duży, aby można było przechowywać ścieżkę do katalogu.</span><span class="sxs-lookup"><span data-stu-id="7a457-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="7a457-126">— lub —</span><span class="sxs-lookup"><span data-stu-id="7a457-126">- or -</span></span><br /><br /> <span data-ttu-id="7a457-127">Bufor wersji nie jest wystarczająco duży, aby można było przechowywać ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="7a457-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a457-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a457-128">Remarks</span></span>  
 <span data-ttu-id="7a457-129">`GetRequestedRuntimeInfo`Metoda zwraca informacje w czasie wykonywania dotyczące wersji załadowanej do procesu, która nie musi być zainstalowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7a457-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="7a457-130">W .NET Framework w wersji 2,0 można uzyskać informacje o najnowszej zainstalowanej wersji za pomocą `GetRequestedRuntimeInfo` metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7a457-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="7a457-131">Określ `pExe` Parametry, `pwszVersion` i `pConfigurationFile` jako wartości null.</span><span class="sxs-lookup"><span data-stu-id="7a457-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="7a457-132">Określ flagę RUNTIME_INFO_UPGRADE_VERSION w `RUNTIME_INFO_FLAGS` wyliczeniach dla `runtimeInfoFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="7a457-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="7a457-133">`GetRequestedRuntimeInfo`Metoda nie zwraca najnowszej wersji środowiska CLR w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="7a457-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="7a457-134">Istnieje plik konfiguracji aplikacji, który określa ładowanie konkretnej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7a457-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="7a457-135">Należy pamiętać, że .NET Framework użyje pliku konfiguracji nawet w przypadku określenia wartości null dla `pConfigurationFile` parametru.</span><span class="sxs-lookup"><span data-stu-id="7a457-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="7a457-136">Wywołana została Metoda [CorBindToRuntimeEx](corbindtoruntimeex-function.md) określająca wcześniejszą wersję środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7a457-136">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="7a457-137">Aplikacja, która została skompilowana dla starszej wersji środowiska CLR, jest obecnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="7a457-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="7a457-138">Dla `runtimeInfoFlags` parametru można określić tylko jedną ze stałych architektury dla `RUNTIME_INFO_FLAGS` wyliczenia jednocześnie:</span><span class="sxs-lookup"><span data-stu-id="7a457-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="7a457-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="7a457-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="7a457-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="7a457-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="7a457-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="7a457-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a457-142">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a457-142">Requirements</span></span>  
 <span data-ttu-id="7a457-143">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a457-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a457-144">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7a457-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a457-145">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7a457-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a457-146">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a457-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a457-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a457-147">See also</span></span>

- [<span data-ttu-id="7a457-148">GetRequestedRuntimeVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7a457-148">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="7a457-149">GetVersionFromProcess, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a457-149">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="7a457-150">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="7a457-150">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
