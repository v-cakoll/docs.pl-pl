---
title: ICLRRuntimeInfo::GetVersionString — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e320936430307dab066eecc835ac5c84bd22bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202329"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="2a370-102">ICLRRuntimeInfo::GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a370-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="2a370-103">Pobiera (CLR) wersja informacje CLR skojarzony z danym [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2a370-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="2a370-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="2a370-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="2a370-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="2a370-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="2a370-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="2a370-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="2a370-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a370-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a370-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a370-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="2a370-109">[out] Kompilacja .NET Framework w wersji w formacie "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="2a370-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="2a370-110">*A*, *B*, i *X* są liczby dziesiętne, które odpowiadają wersji głównej, pomocniczej wersji i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2a370-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="2a370-111">*X* jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="2a370-111">*X* is optional.</span></span> <span data-ttu-id="2a370-112">Jeśli *X* jest nieobecna, jest nie końcowej kropki.</span><span class="sxs-lookup"><span data-stu-id="2a370-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a370-113">Ten parametr musi odpowiadać nazwie katalogu dla .NET Framework w wersji, wyświetlaną w obszarze C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="2a370-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="2a370-114">Przykładowe wartości są "wartości v1.0.3705", "v1.1.4322" i "v2.0.50727" oraz "v4.0. *x*", gdzie *x* zależy od numeru kompilacji zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="2a370-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="2a370-115">Należy zauważyć, że prefiks "v" jest obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="2a370-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="2a370-116">[out w] Określa rozmiar `pwzBuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="2a370-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="2a370-117">Jeśli `pwzBuffer` jest `null`, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer` umożliwia wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="2a370-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a370-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2a370-118">Return Value</span></span>  
 <span data-ttu-id="2a370-119">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="2a370-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2a370-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a370-120">HRESULT</span></span>|<span data-ttu-id="2a370-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2a370-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a370-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a370-122">S_OK</span></span>|<span data-ttu-id="2a370-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2a370-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="2a370-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2a370-124">E_POINTER</span></span>|`pwzBuffer` <span data-ttu-id="2a370-125">lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2a370-125">or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a370-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a370-126">Requirements</span></span>  
 <span data-ttu-id="2a370-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a370-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a370-128">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2a370-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2a370-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a370-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2a370-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2a370-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a370-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a370-131">See also</span></span>

- [<span data-ttu-id="2a370-132">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a370-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="2a370-133">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2a370-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2a370-134">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="2a370-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="2a370-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="2a370-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
