---
title: "IAppDomainBinding::OnAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding.OnAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 131e4af5d8c410f625d2c119097f07f5facd4300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="cf77b-102">IAppDomainBinding::OnAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf77b-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="cf77b-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby powiadomić hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf77b-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf77b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf77b-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf77b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf77b-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="cf77b-106">[in] Wskaźnik do [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) obiekt interfejsu, który reprezentuje nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf77b-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf77b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf77b-107">Requirements</span></span>  
 <span data-ttu-id="cf77b-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf77b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf77b-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf77b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf77b-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf77b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf77b-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf77b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf77b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf77b-112">See Also</span></span>  
 [<span data-ttu-id="cf77b-113">IAppDomainBinding, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf77b-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
