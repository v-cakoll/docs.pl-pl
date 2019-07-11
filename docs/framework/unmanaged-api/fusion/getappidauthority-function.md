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
ms.openlocfilehash: 536f3249593333234f7f09921007b483fb80cf79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778591"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="7984e-102">GetAppIdAuthority — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7984e-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="7984e-103">Pobiera wskaźnik do [iappidauthority —](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) wystąpienie, które zarządza kluczami, dokumentacji i tożsamości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7984e-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7984e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7984e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7984e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7984e-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="7984e-106">[out] Zwrócony `IAppIdAuthority` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="7984e-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7984e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7984e-107">Requirements</span></span>  
 <span data-ttu-id="7984e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7984e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7984e-109">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="7984e-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7984e-110">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7984e-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7984e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7984e-111">See also</span></span>

- [<span data-ttu-id="7984e-112">IAppIdAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="7984e-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="7984e-113">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7984e-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
