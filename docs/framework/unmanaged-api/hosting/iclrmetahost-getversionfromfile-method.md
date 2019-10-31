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
ms.openlocfilehash: a237dff63015cda2cf2ca86a64bb4028ec9b6e2c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140919"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="555ca-102">ICLRMetaHost::GetVersionFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="555ca-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="555ca-103">Pobiera oryginalną wersję kompilacji .NET Framework zestawu (przechowywaną w metadanych), uwzględniając ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="555ca-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="555ca-104">Ta metoda zastępuje funkcję [GetFileVersion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="555ca-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="555ca-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="555ca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="555ca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="555ca-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="555ca-107">podczas Pełna ścieżka pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="555ca-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="555ca-108">określoną Wersja kompilacji .NET Framework przechowywana w metadanych w formacie "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="555ca-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="555ca-109">*A*, *B*i *X* to liczby dziesiętne, które odpowiadają wersji głównej, wersji pomocniczej i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="555ca-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="555ca-110">Długość tego ciągu jest ograniczona do wartości MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="555ca-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="555ca-111">Dane wyjściowe są zgodne z nazwą katalogu dla .NET Framework wersji, ponieważ pojawia się w obszarze C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="555ca-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="555ca-112">Przykładowe wartości to "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" i "v 4.0. *X*", gdzie *x* zależy od zainstalowanego numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="555ca-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="555ca-113">Należy zauważyć, że prefiks "v" jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="555ca-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="555ca-114">[in. out] Rozmiar `pwzbuffer`, aby uniknąć przekroczeń buforu.</span><span class="sxs-lookup"><span data-stu-id="555ca-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="555ca-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="555ca-115">Return Value</span></span>  
 <span data-ttu-id="555ca-116">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="555ca-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="555ca-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="555ca-117">HRESULT</span></span>|<span data-ttu-id="555ca-118">Opis</span><span class="sxs-lookup"><span data-stu-id="555ca-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="555ca-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="555ca-119">S_OK</span></span>|<span data-ttu-id="555ca-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="555ca-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="555ca-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="555ca-121">E_POINTER</span></span>|<span data-ttu-id="555ca-122">`pwzbuffer` lub `pcchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="555ca-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="555ca-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="555ca-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="555ca-124">Bufor jest za mały.</span><span class="sxs-lookup"><span data-stu-id="555ca-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="555ca-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="555ca-125">Requirements</span></span>  
 <span data-ttu-id="555ca-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="555ca-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="555ca-127">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="555ca-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="555ca-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="555ca-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="555ca-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="555ca-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555ca-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="555ca-130">See also</span></span>

- [<span data-ttu-id="555ca-131">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="555ca-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="555ca-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="555ca-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
