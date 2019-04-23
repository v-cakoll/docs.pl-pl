---
title: ICLRMetaHost::GetVersionFromFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6c7fd48269a3e8291a548b3e13efe5c8e70652
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150816"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="49b27-102">ICLRMetaHost::GetVersionFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="49b27-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="49b27-103">Pobiera zestaw oryginalna wersja programu .NET Framework kompilacji (przechowywany w metadanych) podanej ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="49b27-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="49b27-104">Ta metoda zastępuje [getfileversion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="49b27-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b27-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="49b27-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49b27-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="49b27-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="49b27-107">[in] Ścieżka pliku kompletny zestaw.</span><span class="sxs-lookup"><span data-stu-id="49b27-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="49b27-108">[out] Wersja kompilacji programu .NET Framework, które są przechowywane w metadanych, w formacie "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="49b27-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="49b27-109">*A*, *B*, i *X* są liczby dziesiętne, które odpowiadają wersji głównej, pomocniczej wersji i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="49b27-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="49b27-110">Długość tego ciągu jest ograniczona do MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="49b27-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49b27-111">Te dane wyjściowe odpowiada nazwę katalogu .NET Framework w wersji wyświetlaną w obszarze C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="49b27-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="49b27-112">Przykładowe wartości są "wartości v1.0.3705", "v1.1.4322" i "v2.0.50727" oraz "v4.0. *X*", gdzie *X* zależy od numeru kompilacji zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="49b27-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="49b27-113">Należy pamiętać, że jest wymagany prefiks "v".</span><span class="sxs-lookup"><span data-stu-id="49b27-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="49b27-114">[out w] Rozmiar `pwzbuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="49b27-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49b27-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49b27-115">Return Value</span></span>  
 <span data-ttu-id="49b27-116">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="49b27-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="49b27-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49b27-117">HRESULT</span></span>|<span data-ttu-id="49b27-118">Opis</span><span class="sxs-lookup"><span data-stu-id="49b27-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49b27-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="49b27-119">S_OK</span></span>|<span data-ttu-id="49b27-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="49b27-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="49b27-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="49b27-121">E_POINTER</span></span>|<span data-ttu-id="49b27-122">`pwzbuffer` lub `pcchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="49b27-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="49b27-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="49b27-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="49b27-124">Bufor jest za mały.</span><span class="sxs-lookup"><span data-stu-id="49b27-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49b27-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49b27-125">Requirements</span></span>  
 <span data-ttu-id="49b27-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49b27-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49b27-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="49b27-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="49b27-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49b27-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49b27-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49b27-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b27-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49b27-130">See also</span></span>

- [<span data-ttu-id="49b27-131">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="49b27-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="49b27-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="49b27-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
