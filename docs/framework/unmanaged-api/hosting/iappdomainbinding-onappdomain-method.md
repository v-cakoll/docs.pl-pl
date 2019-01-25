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
ms.openlocfilehash: 8dfd396568424c3a2300ed5d982e766afd5f925f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725496"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="00f93-102">IAppDomainBinding::OnAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="00f93-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="00f93-103">Metoda wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) w celu powiadomienia hosta, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00f93-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00f93-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00f93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00f93-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="00f93-106">[in] Wskaźnik do [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) obiektu interfejsu, który reprezentuje nową domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00f93-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f93-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00f93-107">Requirements</span></span>  
 <span data-ttu-id="00f93-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00f93-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f93-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00f93-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00f93-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00f93-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00f93-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f93-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f93-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00f93-112">See also</span></span>
- [<span data-ttu-id="00f93-113">IAppDomainBinding, interfejs</span><span class="sxs-lookup"><span data-stu-id="00f93-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
