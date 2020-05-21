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
ms.openlocfilehash: ccf48b6aea25bd602b55727c2e5958811702f6bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762581"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="67d5d-102">ICLRRuntimeInfo::GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="67d5d-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="67d5d-103">Pobiera informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) skojarzone z danym interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="67d5d-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="67d5d-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="67d5d-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="67d5d-105">GetRequestedRuntimeInfo —</span><span class="sxs-lookup"><span data-stu-id="67d5d-105">GetRequestedRuntimeInfo</span></span>](getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="67d5d-106">GetRequestedRuntimeVersion —</span><span class="sxs-lookup"><span data-stu-id="67d5d-106">GetRequestedRuntimeVersion</span></span>](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="67d5d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="67d5d-107">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67d5d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="67d5d-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="67d5d-109">określoną Wersja kompilacji .NET Framework w formacie "v*A*. *B*[.\* X\*] ".</span><span class="sxs-lookup"><span data-stu-id="67d5d-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="67d5d-110">*A*, *B*i *X* to liczby dziesiętne, które odpowiadają wersji głównej, wersji pomocniczej i numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="67d5d-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="67d5d-111">*Symbol X* jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67d5d-111">*X* is optional.</span></span> <span data-ttu-id="67d5d-112">Jeśli *X* nie istnieje, nie ma końcowej kropki.</span><span class="sxs-lookup"><span data-stu-id="67d5d-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67d5d-113">Ten parametr musi być zgodny z nazwą katalogu dla .NET Framework wersji, ponieważ pojawia się w obszarze C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="67d5d-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="67d5d-114">Przykładowe wartości to "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" i "v 4.0. *x*", gdzie *x* zależy od zainstalowanego numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="67d5d-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="67d5d-115">Należy zauważyć, że prefiks "v" jest obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="67d5d-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="67d5d-116">[in. out] Określa rozmiar, `pwzBuffer` Aby zapobiec przekroczeniu buforu.</span><span class="sxs-lookup"><span data-stu-id="67d5d-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="67d5d-117">Jeśli `pwzBuffer` jest `null` , `pchBuffer` zwraca wymagany rozmiar, `pwzBuffer` Aby umożliwić wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="67d5d-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67d5d-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="67d5d-118">Return Value</span></span>  
 <span data-ttu-id="67d5d-119">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="67d5d-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="67d5d-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67d5d-120">HRESULT</span></span>|<span data-ttu-id="67d5d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="67d5d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67d5d-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="67d5d-122">S_OK</span></span>|<span data-ttu-id="67d5d-123">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="67d5d-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="67d5d-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="67d5d-124">E_POINTER</span></span>|<span data-ttu-id="67d5d-125">`pwzBuffer`lub `pchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="67d5d-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67d5d-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67d5d-126">Requirements</span></span>  
 <span data-ttu-id="67d5d-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67d5d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d5d-128">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="67d5d-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="67d5d-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="67d5d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67d5d-130">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d5d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d5d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67d5d-131">See also</span></span>

- [<span data-ttu-id="67d5d-132">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="67d5d-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="67d5d-133">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="67d5d-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="67d5d-134">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="67d5d-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="67d5d-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="67d5d-135">Hosting</span></span>](index.md)
