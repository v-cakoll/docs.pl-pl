---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 647c87b6f42b01922a385d502d72410af3140cd2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771790"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="05179-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda</span><span class="sxs-lookup"><span data-stu-id="05179-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="05179-103">Wiąże bieżącego środowiska uruchomieniowego dla wszystkich starszych wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w wersji 2 aktywacji decyzji dotyczących zasad.</span><span class="sxs-lookup"><span data-stu-id="05179-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05179-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05179-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05179-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05179-105">Return Value</span></span>  
 <span data-ttu-id="05179-106">Ta metoda zwraca następujące specyficzne wyniki HRESULT:</span><span class="sxs-lookup"><span data-stu-id="05179-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="05179-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05179-107">HRESULT</span></span>|<span data-ttu-id="05179-108">Opis</span><span class="sxs-lookup"><span data-stu-id="05179-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05179-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="05179-109">S_OK</span></span>|<span data-ttu-id="05179-110">Wiązanie zakończyło się pomyślnie lub tego środowiska wykonawczego został już powiązany jako starszych wersji 2 aktywacji zasad środowisko uruchomieniowe CLR.</span><span class="sxs-lookup"><span data-stu-id="05179-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="05179-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="05179-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="05179-112">Środowiskiem uruchomieniowym w różnych była już powiązana starsze zasady 2 aktywacji wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="05179-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05179-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05179-113">Remarks</span></span>  
 <span data-ttu-id="05179-114">Jeśli bieżącego środowiska uruchomieniowego jest już powiązany dla wszystkich starszej wersji środowiska CLR w wersji 2 aktywacji decyzji dotyczących zasad (na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu na [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracyjnym), ta metoda Zwraca wynik błędu; Zamiast tego wynik jest S_OK, tak, jak możesz ją, jeśli metoda było pomyślnie powiązane zasady aktywacji starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="05179-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05179-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05179-115">Requirements</span></span>  
 <span data-ttu-id="05179-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05179-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05179-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="05179-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="05179-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05179-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05179-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05179-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05179-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05179-120">See also</span></span>

- [<span data-ttu-id="05179-121">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="05179-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="05179-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="05179-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="05179-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="05179-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="05179-124">\<Uruchamianie > Element</span><span class="sxs-lookup"><span data-stu-id="05179-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
