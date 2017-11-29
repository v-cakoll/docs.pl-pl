---
title: "ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="e5dd2-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5dd2-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="e5dd2-103">Zwraca interfejs, który reprezentuje runtime, do którego zasad aktywacji starszych wersji został powiązany, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis pliku konfiguracji, używając bezpośredniego aktywacji starszych interfejsów API, przez wywołanie [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5dd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5dd2-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5dd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5dd2-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="e5dd2-106">[in] Required.Currently jest jedyną poprawną wartością dla tego parametru `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="e5dd2-107">[out] Wymagane.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-107">[out] Required.</span></span> <span data-ttu-id="e5dd2-108">Gdy metoda zwróci wartość, zawiera wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który reprezentuje środowiska uruchomieniowego, która została powiązana z zasad aktywacji starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5dd2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e5dd2-109">Return Value</span></span>  
 <span data-ttu-id="e5dd2-110">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e5dd2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5dd2-111">HRESULT</span></span>|<span data-ttu-id="e5dd2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e5dd2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5dd2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5dd2-113">S_OK</span></span>|<span data-ttu-id="e5dd2-114">Metoda została ukończona pomyślnie i zwrócił środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="e5dd2-115">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e5dd2-115">S_FALSE</span></span>|<span data-ttu-id="e5dd2-116">Metoda zakończyła się pomyślnie, ale starszej wersji środowiska uruchomieniowego ma nie jeszcze został powiązany.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="e5dd2-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e5dd2-117">E_NOINTERFACE</span></span>|<span data-ttu-id="e5dd2-118">Metoda znaleziono środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszych wersji, ale `riid` nie jest obsługiwany przez ten program obsługi.</span><span class="sxs-lookup"><span data-stu-id="e5dd2-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5dd2-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5dd2-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5dd2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5dd2-120">Requirements</span></span>  
 <span data-ttu-id="e5dd2-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5dd2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5dd2-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e5dd2-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e5dd2-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5dd2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5dd2-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5dd2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dd2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5dd2-125">See Also</span></span>  
 [<span data-ttu-id="e5dd2-126">ICLRMetaHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="e5dd2-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="e5dd2-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="e5dd2-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
