---
title: "ICLRRuntimeInfo::GetVersionString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ae6f21fac359006b6d2e56fdd4ba50fb18bb972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="a00d5-102">ICLRRuntimeInfo::GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="a00d5-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="a00d5-103">Pobiera wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) informacje o wersji skojarzone z danym [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a00d5-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a00d5-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a00d5-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="a00d5-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a00d5-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="a00d5-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="a00d5-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="a00d5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a00d5-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a00d5-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="a00d5-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="a00d5-109">[out] .NET Framework w wersji kompilacji w formacie "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="a00d5-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="a00d5-110">*A*, *B*, i *X* są liczbami dziesiętnymi, które odpowiadają wersji głównej, wersja pomocnicza i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a00d5-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="a00d5-111">*X* jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a00d5-111">*X* is optional.</span></span> <span data-ttu-id="a00d5-112">Jeśli *X* jest nieobecna, jest nie końcowej kropki.</span><span class="sxs-lookup"><span data-stu-id="a00d5-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a00d5-113">Ten parametr musi być zgodna nazwę katalogu .NET Framework w wersji, która jest wyświetlana w obszarze C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="a00d5-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="a00d5-114">Przykładowe wartości to "v1.0.3705", "v1.1.4322", "v2.0.50727" i "v4.0. *x*", gdzie *x* zależy od numeru kompilacji zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="a00d5-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="a00d5-115">Należy pamiętać, że prefiksu "v" jest obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="a00d5-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="a00d5-116">[w, out] Określa rozmiar `pwzBuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="a00d5-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="a00d5-117">Jeśli `pwzBuffer` jest `null`, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer` umożliwia wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="a00d5-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a00d5-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a00d5-118">Return Value</span></span>  
 <span data-ttu-id="a00d5-119">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a00d5-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a00d5-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a00d5-120">HRESULT</span></span>|<span data-ttu-id="a00d5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d5-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a00d5-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="a00d5-122">S_OK</span></span>|<span data-ttu-id="a00d5-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a00d5-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="a00d5-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a00d5-124">E_POINTER</span></span>|<span data-ttu-id="a00d5-125">`pwzBuffer`lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a00d5-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a00d5-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a00d5-126">Requirements</span></span>  
 <span data-ttu-id="a00d5-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a00d5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00d5-128">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a00d5-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a00d5-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a00d5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a00d5-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00d5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00d5-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a00d5-131">See Also</span></span>  
 [<span data-ttu-id="a00d5-132">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a00d5-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="a00d5-133">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a00d5-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a00d5-134">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="a00d5-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="a00d5-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="a00d5-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
