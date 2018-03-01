---
title: "GetIdentityAuthority — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5fab6fa7c8e58dcd2fdece05572242230847f62f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="a9440-102">GetIdentityAuthority — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a9440-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="a9440-103">Pobiera wskaźnik do [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) wystąpienia zarządzanego klucze obiekty kod.</span><span class="sxs-lookup"><span data-stu-id="a9440-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9440-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9440-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9440-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9440-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="a9440-106">[out] Zwrócona `IIdentityAuthority` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a9440-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9440-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9440-107">Requirements</span></span>  
 <span data-ttu-id="a9440-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9440-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9440-109">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a9440-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a9440-110">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9440-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9440-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9440-111">See Also</span></span>  
 [<span data-ttu-id="a9440-112">IIdentityAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9440-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 [<span data-ttu-id="a9440-113">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="a9440-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
