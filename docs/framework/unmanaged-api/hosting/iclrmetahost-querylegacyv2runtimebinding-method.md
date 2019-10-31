---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: 90474a61b16d65565889bd69ef75616804d8bc60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140882"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="83f62-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda</span><span class="sxs-lookup"><span data-stu-id="83f62-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="83f62-103">Zwraca interfejs, który reprezentuje środowisko uruchomieniowe, do którego powiązano starsze zasady aktywacji, na przykład przy użyciu atrybutu `useLegacyV2RuntimeActivationPolicy` w wpisie pliku konfiguracji [elementu > start\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , przez bezpośrednie użycie starszych interfejsów API aktywacji lub wywołując metodę [ICLRRuntimeInfo:: BindAsLegacyV2Runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83f62-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83f62-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83f62-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="83f62-106">podczas Wymagane. obecnie jedyną prawidłową wartością tego parametru jest `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="83f62-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="83f62-107">określoną Wymagane.</span><span class="sxs-lookup"><span data-stu-id="83f62-107">[out] Required.</span></span> <span data-ttu-id="83f62-108">Gdy ta metoda zwraca, zawiera wskaźnik do interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który reprezentuje środowisko uruchomieniowe, które zostało powiązane ze starszymi zasadami aktywacji.</span><span class="sxs-lookup"><span data-stu-id="83f62-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83f62-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83f62-109">Return Value</span></span>  
 <span data-ttu-id="83f62-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="83f62-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="83f62-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83f62-111">HRESULT</span></span>|<span data-ttu-id="83f62-112">Opis</span><span class="sxs-lookup"><span data-stu-id="83f62-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83f62-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="83f62-113">S_OK</span></span>|<span data-ttu-id="83f62-114">Metoda została zakończona pomyślnie i zwróciło środowisko uruchomieniowe, które było powiązane ze starszymi zasadami aktywacji.</span><span class="sxs-lookup"><span data-stu-id="83f62-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="83f62-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="83f62-115">S_FALSE</span></span>|<span data-ttu-id="83f62-116">Metoda została ukończona pomyślnie, ale starsze środowisko uruchomieniowe nie zostało jeszcze powiązane.</span><span class="sxs-lookup"><span data-stu-id="83f62-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="83f62-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="83f62-117">E_NOINTERFACE</span></span>|<span data-ttu-id="83f62-118">Metoda znalazła środowisko uruchomieniowe powiązane ze starszymi zasadami aktywacji, ale `riid` nie jest obsługiwane przez to środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="83f62-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83f62-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83f62-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f62-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83f62-120">Requirements</span></span>  
 <span data-ttu-id="83f62-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f62-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f62-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="83f62-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="83f62-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83f62-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83f62-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f62-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f62-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83f62-125">See also</span></span>

- [<span data-ttu-id="83f62-126">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="83f62-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="83f62-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="83f62-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
