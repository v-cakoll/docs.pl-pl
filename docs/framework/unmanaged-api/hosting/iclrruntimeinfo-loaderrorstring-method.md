---
title: ICLRRuntimeInfo::LoadErrorString — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a565c19285b00c807ef6fbfc018a40467139638e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466352"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="77259-102">ICLRRuntimeInfo::LoadErrorString — Metoda</span><span class="sxs-lookup"><span data-stu-id="77259-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="77259-103">Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="77259-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="77259-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="77259-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="77259-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="77259-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="77259-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="77259-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="77259-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="77259-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77259-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="77259-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="77259-109">[in] Wartość HRESULT do translacji.</span><span class="sxs-lookup"><span data-stu-id="77259-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="77259-110">[out] Ciąg komunikatu skojarzonego z danym elementem HRESULT.</span><span class="sxs-lookup"><span data-stu-id="77259-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="77259-111">[out w] Rozmiar `pwzbuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="77259-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="77259-112">Jeśli `pwzbuffer` ma wartość null, `pcchBuffer` zawiera oczekiwanego rozmiaru `pwzbuffer` umożliwia wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="77259-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="77259-113">[in] Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="77259-113">[in] The culture identifier.</span></span> <span data-ttu-id="77259-114">Aby użyć domyślnej kultury, należy określić -1.</span><span class="sxs-lookup"><span data-stu-id="77259-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77259-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77259-115">Return Value</span></span>  
 <span data-ttu-id="77259-116">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="77259-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="77259-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77259-117">HRESULT</span></span>|<span data-ttu-id="77259-118">Opis</span><span class="sxs-lookup"><span data-stu-id="77259-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77259-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="77259-119">S_OK</span></span>|<span data-ttu-id="77259-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="77259-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="77259-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="77259-121">E_POINTER</span></span>|<span data-ttu-id="77259-122">`pcchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="77259-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="77259-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="77259-123">E_INVALIDARG</span></span>|<span data-ttu-id="77259-124">`pwzBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="77259-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77259-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77259-125">Requirements</span></span>  
 <span data-ttu-id="77259-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77259-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77259-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="77259-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77259-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77259-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77259-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77259-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77259-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77259-130">See also</span></span>
- [<span data-ttu-id="77259-131">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="77259-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="77259-132">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="77259-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="77259-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="77259-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
