---
title: GetAppIdAuthority — Funkcja
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274b91793cd51348c42661bf12a4e4385e17f630
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093972"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="374ce-102">GetAppIdAuthority — Funkcja</span><span class="sxs-lookup"><span data-stu-id="374ce-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="374ce-103">Pobiera wskaźnik do [iappidauthority —](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) wystąpienie, które zarządza kluczami, dokumentacji i tożsamości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="374ce-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="374ce-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="374ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="374ce-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="374ce-106">[out] Zwrócony `IAppIdAuthority` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="374ce-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="374ce-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="374ce-107">Requirements</span></span>  
 <span data-ttu-id="374ce-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="374ce-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="374ce-109">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="374ce-109">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="374ce-110">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="374ce-110">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="374ce-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="374ce-111">See also</span></span>

- [<span data-ttu-id="374ce-112">IAppIdAuthority — Interfejs</span><span class="sxs-lookup"><span data-stu-id="374ce-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="374ce-113">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="374ce-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
