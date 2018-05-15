---
title: IAppDomainBinding::OnAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5db040f6db078b211043c547eed823c9b495ac97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="36c37-102">IAppDomainBinding::OnAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="36c37-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="36c37-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby powiadomić hosta utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36c37-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36c37-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36c37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36c37-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="36c37-106">[in] Wskaźnik do [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) obiekt interfejsu, który reprezentuje nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36c37-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c37-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36c37-107">Requirements</span></span>  
 <span data-ttu-id="36c37-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c37-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c37-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36c37-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36c37-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36c37-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36c37-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c37-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c37-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36c37-112">See Also</span></span>  
 [<span data-ttu-id="36c37-113">IAppDomainBinding, interfejs</span><span class="sxs-lookup"><span data-stu-id="36c37-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
