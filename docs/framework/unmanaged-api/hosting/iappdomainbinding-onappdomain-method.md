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
ms.openlocfilehash: 523f90966501e06994fb0e11b3c77aa62c378eef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770462"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="03ad1-102">IAppDomainBinding::OnAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="03ad1-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="03ad1-103">Metoda wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) w celu powiadomienia hosta, że utworzono domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03ad1-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ad1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03ad1-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03ad1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03ad1-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="03ad1-106">[in] Wskaźnik do [IUnknown](/cpp/atl/iunknown) obiektu interfejsu, który reprezentuje nową domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03ad1-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ad1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03ad1-107">Requirements</span></span>  
 <span data-ttu-id="03ad1-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03ad1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ad1-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03ad1-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03ad1-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03ad1-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03ad1-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ad1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ad1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03ad1-112">See also</span></span>

- [<span data-ttu-id="03ad1-113">IAppDomainBinding, interfejs</span><span class="sxs-lookup"><span data-stu-id="03ad1-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
