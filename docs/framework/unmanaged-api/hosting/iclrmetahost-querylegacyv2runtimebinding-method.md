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
ms.openlocfilehash: b9a51a85bd17e527d4c04b69ca65100a7069607f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703716"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="46bca-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda</span><span class="sxs-lookup"><span data-stu-id="46bca-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="46bca-103">Zwraca interfejs, który reprezentuje środowisko uruchomieniowe, do którego zostały powiązane starsze zasady aktywacji, na przykład przy użyciu `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w ICLRRuntimeInfo wpis pliku konfiguracji elementu, bezpośrednio wykorzystując starsze interfejsy API aktywacji lub wywołując metodę [BindAsLegacyV2Runtime —:](iclrruntimeinfo-bindaslegacyv2runtime-method.md)</span><span class="sxs-lookup"><span data-stu-id="46bca-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46bca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46bca-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46bca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46bca-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="46bca-106">podczas Wymagane. obecnie jedyną prawidłową wartością tego parametru jest `IID_ICLRRuntimeInfo` .</span><span class="sxs-lookup"><span data-stu-id="46bca-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="46bca-107">określoną Wymagane.</span><span class="sxs-lookup"><span data-stu-id="46bca-107">[out] Required.</span></span> <span data-ttu-id="46bca-108">Gdy ta metoda zwraca, zawiera wskaźnik do interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , który reprezentuje środowisko uruchomieniowe, które zostało powiązane ze starszymi zasadami aktywacji.</span><span class="sxs-lookup"><span data-stu-id="46bca-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46bca-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="46bca-109">Return Value</span></span>  
 <span data-ttu-id="46bca-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="46bca-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="46bca-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46bca-111">HRESULT</span></span>|<span data-ttu-id="46bca-112">Opis</span><span class="sxs-lookup"><span data-stu-id="46bca-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46bca-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="46bca-113">S_OK</span></span>|<span data-ttu-id="46bca-114">Metoda została zakończona pomyślnie i zwróciło środowisko uruchomieniowe, które było powiązane ze starszymi zasadami aktywacji.</span><span class="sxs-lookup"><span data-stu-id="46bca-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="46bca-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="46bca-115">S_FALSE</span></span>|<span data-ttu-id="46bca-116">Metoda została ukończona pomyślnie, ale starsze środowisko uruchomieniowe nie zostało jeszcze powiązane.</span><span class="sxs-lookup"><span data-stu-id="46bca-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="46bca-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="46bca-117">E_NOINTERFACE</span></span>|<span data-ttu-id="46bca-118">Metoda znalazła środowisko uruchomieniowe powiązane ze starszymi zasadami aktywacji, ale `riid` nie jest obsługiwane przez to środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="46bca-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46bca-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46bca-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46bca-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46bca-120">Requirements</span></span>  
 <span data-ttu-id="46bca-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46bca-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46bca-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="46bca-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="46bca-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46bca-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46bca-124">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46bca-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46bca-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46bca-125">See also</span></span>

- [<span data-ttu-id="46bca-126">ICLRMetaHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="46bca-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="46bca-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="46bca-127">Hosting</span></span>](index.md)
