---
title: "ICLRRuntimeInfo::LoadErrorString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadErrorString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26fa051e5c4735307edbb443e6615a57190c0ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="a7491-102">ICLRRuntimeInfo::LoadErrorString — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7491-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="a7491-103">Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="a7491-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="a7491-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a7491-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="a7491-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="a7491-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="a7491-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="a7491-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="a7491-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7491-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7491-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7491-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="a7491-109">[in] HRESULT do tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="a7491-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a7491-110">[out] Ciąg komunikatu skojarzone z danym HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a7491-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="a7491-111">[w, out] Rozmiar `pwzbuffer` w celu uniknięcia przepełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="a7491-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="a7491-112">Jeśli `pwzbuffer` ma wartość null, `pcchBuffer` zawiera oczekiwanego rozmiaru `pwzbuffer` umożliwia wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="a7491-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="a7491-113">[in] Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="a7491-113">[in] The culture identifier.</span></span> <span data-ttu-id="a7491-114">Aby użyć kultury domyślnej, należy określić wartość -1.</span><span class="sxs-lookup"><span data-stu-id="a7491-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7491-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7491-115">Return Value</span></span>  
 <span data-ttu-id="a7491-116">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a7491-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a7491-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7491-117">HRESULT</span></span>|<span data-ttu-id="a7491-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a7491-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7491-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7491-119">S_OK</span></span>|<span data-ttu-id="a7491-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7491-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="a7491-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a7491-121">E_POINTER</span></span>|<span data-ttu-id="a7491-122">`pcchBuffer`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a7491-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="a7491-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a7491-123">E_INVALIDARG</span></span>|<span data-ttu-id="a7491-124">`pwzBuffer`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a7491-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7491-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7491-125">Requirements</span></span>  
 <span data-ttu-id="a7491-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7491-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7491-127">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a7491-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a7491-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7491-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7491-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7491-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7491-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7491-130">See Also</span></span>  
 [<span data-ttu-id="a7491-131">ICLRRuntimeInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7491-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="a7491-132">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7491-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a7491-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="a7491-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
