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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7312a50137ab8a5c066d5e140a1742ee1918b44
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776559"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="9067d-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda</span><span class="sxs-lookup"><span data-stu-id="9067d-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="9067d-103">Zwraca interfejs, który reprezentuje środowiska uruchomieniowego, do którego zasady starszych aktywacji została powiązana, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu na [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis w pliku konfiguracji, przy użyciu bezpośredniego Aktywacja starszych interfejsów API lub przez wywołanie metody [iclrruntimeinfo::bindaslegacyv2runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9067d-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9067d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9067d-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9067d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9067d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="9067d-106">[in] Jedyna prawidłowa wartość dla tego parametru to Required.Currently `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="9067d-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="9067d-107">[out] Wymagane.</span><span class="sxs-lookup"><span data-stu-id="9067d-107">[out] Required.</span></span> <span data-ttu-id="9067d-108">Po powrocie z tej metody zawiera wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który reprezentuje powiązanej z zasad aktywacji starszej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9067d-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9067d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9067d-109">Return Value</span></span>  
 <span data-ttu-id="9067d-110">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9067d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9067d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9067d-111">HRESULT</span></span>|<span data-ttu-id="9067d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9067d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9067d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9067d-113">S_OK</span></span>|<span data-ttu-id="9067d-114">Metoda została ukończona pomyślnie i zwrócony środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9067d-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="9067d-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9067d-115">S_FALSE</span></span>|<span data-ttu-id="9067d-116">Metoda została ukończona pomyślnie, ale starszej wersji środowiska uruchomieniowego nie została jeszcze powiązana.</span><span class="sxs-lookup"><span data-stu-id="9067d-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="9067d-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="9067d-117">E_NOINTERFACE</span></span>|<span data-ttu-id="9067d-118">Metoda znaleziono środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszej wersji, ale `riid` nie jest obsługiwany przez ten program obsługi.</span><span class="sxs-lookup"><span data-stu-id="9067d-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9067d-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9067d-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9067d-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9067d-120">Requirements</span></span>  
 <span data-ttu-id="9067d-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9067d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9067d-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9067d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9067d-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9067d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9067d-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9067d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9067d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9067d-125">See also</span></span>

- [<span data-ttu-id="9067d-126">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9067d-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="9067d-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="9067d-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
