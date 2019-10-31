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
ms.openlocfilehash: 37c02b878cd52034603ab6cafe4d8aaca594cbe9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126889"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="8b5b3-102">IAppDomainBinding::OnAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b5b3-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="8b5b3-103">Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR) do powiadamiania hosta o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b5b3-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5b3-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b5b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b5b3-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="8b5b3-106">podczas Wskaźnik do obiektu interfejsu [IUnknown](/cpp/atl/iunknown) , który reprezentuje nową domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b5b3-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5b3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b5b3-107">Requirements</span></span>  
 <span data-ttu-id="8b5b3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5b3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5b3-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b5b3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b5b3-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b5b3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b5b3-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5b3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5b3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b5b3-112">See also</span></span>

- [<span data-ttu-id="8b5b3-113">IAppDomainBinding, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b5b3-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
