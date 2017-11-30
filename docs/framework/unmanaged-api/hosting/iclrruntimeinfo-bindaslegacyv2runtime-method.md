---
title: "ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 229c5483c02357054f3d2821d8e024c78887e839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="d027e-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda</span><span class="sxs-lookup"><span data-stu-id="d027e-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="d027e-103">Wiąże bieżącego środowiska uruchomieniowego dla wszystkich starszych wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w wersji 2 aktywacji decyzji dotyczących zasad.</span><span class="sxs-lookup"><span data-stu-id="d027e-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d027e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d027e-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d027e-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d027e-105">Return Value</span></span>  
 <span data-ttu-id="d027e-106">Ta metoda zwraca następujące określonych wyników HRESULT:</span><span class="sxs-lookup"><span data-stu-id="d027e-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="d027e-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d027e-107">HRESULT</span></span>|<span data-ttu-id="d027e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d027e-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d027e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="d027e-109">S_OK</span></span>|<span data-ttu-id="d027e-110">Wiązanie zakończyło się pomyślnie albo tego środowiska wykonawczego został już powiązany jako starszych wersji 2 aktywacji zasad środowisko uruchomieniowe CLR.</span><span class="sxs-lookup"><span data-stu-id="d027e-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="d027e-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="d027e-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="d027e-112">Różne środowiska wykonawczego został już powiązany z starszej wersji zasad 2 aktywacji wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d027e-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d027e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d027e-113">Remarks</span></span>  
 <span data-ttu-id="d027e-114">Jeśli bieżącego środowiska uruchomieniowego jest już powiązany dla wszystkich starszej wersji środowiska CLR w wersji 2 aktywacji decyzji dotyczących zasad (na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<uruchamiania > elementu](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracji), metoda Zwraca wynik błędu; Zamiast tego wynikiem jest wartość S_OK, tak samo, jak możesz ją, jeśli metoda ma pomyślnie powiązany zasad aktywacji starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="d027e-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d027e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d027e-115">Requirements</span></span>  
 <span data-ttu-id="d027e-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d027e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d027e-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d027e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d027e-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d027e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d027e-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d027e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d027e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d027e-120">See Also</span></span>  
 [<span data-ttu-id="d027e-121">ICLRRuntimeInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="d027e-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="d027e-122">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="d027e-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d027e-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="d027e-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="d027e-124">\<Uruchamianie > — Element</span><span class="sxs-lookup"><span data-stu-id="d027e-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
