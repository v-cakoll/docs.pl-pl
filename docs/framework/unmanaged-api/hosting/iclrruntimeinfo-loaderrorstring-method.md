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
ms.openlocfilehash: b485811b0e7d2f657ff2d2c1d7a2aa135e48a335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771673"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="03c54-102">ICLRRuntimeInfo::LoadErrorString — Metoda</span><span class="sxs-lookup"><span data-stu-id="03c54-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="03c54-103">Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="03c54-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="03c54-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="03c54-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="03c54-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="03c54-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="03c54-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="03c54-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="03c54-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="03c54-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03c54-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="03c54-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="03c54-109">[in] Wartość HRESULT do translacji.</span><span class="sxs-lookup"><span data-stu-id="03c54-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="03c54-110">[out] Ciąg komunikatu skojarzonego z danym elementem HRESULT.</span><span class="sxs-lookup"><span data-stu-id="03c54-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="03c54-111">[out w] Rozmiar `pwzbuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="03c54-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="03c54-112">Jeśli `pwzbuffer` ma wartość null, `pcchBuffer` zawiera oczekiwanego rozmiaru `pwzbuffer` umożliwia wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="03c54-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="03c54-113">[in] Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="03c54-113">[in] The culture identifier.</span></span> <span data-ttu-id="03c54-114">Aby użyć domyślnej kultury, należy określić -1.</span><span class="sxs-lookup"><span data-stu-id="03c54-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03c54-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03c54-115">Return Value</span></span>  
 <span data-ttu-id="03c54-116">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="03c54-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="03c54-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03c54-117">HRESULT</span></span>|<span data-ttu-id="03c54-118">Opis</span><span class="sxs-lookup"><span data-stu-id="03c54-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03c54-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="03c54-119">S_OK</span></span>|<span data-ttu-id="03c54-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="03c54-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="03c54-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="03c54-121">E_POINTER</span></span>|<span data-ttu-id="03c54-122">`pcchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="03c54-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="03c54-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="03c54-123">E_INVALIDARG</span></span>|<span data-ttu-id="03c54-124">`pwzBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="03c54-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03c54-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03c54-125">Requirements</span></span>  
 <span data-ttu-id="03c54-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03c54-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03c54-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="03c54-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03c54-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03c54-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03c54-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03c54-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c54-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03c54-130">See also</span></span>

- [<span data-ttu-id="03c54-131">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="03c54-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="03c54-132">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="03c54-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="03c54-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="03c54-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
