---
title: GetIdentityAuthority — Funkcja
ms.date: 03/30/2017
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
ms.openlocfilehash: acb80f3cc199d4d9f774cb3898335d26fe44b807
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127145"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="0c108-102">GetIdentityAuthority — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0c108-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="0c108-103">Pobiera wskaźnik do wystąpienia [IIdentityAuthority —](iidentityauthority-interface.md) , które zarządza kluczami obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="0c108-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c108-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c108-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c108-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c108-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="0c108-106">określoną Zwrócony wskaźnik `IIdentityAuthority`.</span><span class="sxs-lookup"><span data-stu-id="0c108-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c108-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c108-107">Requirements</span></span>  
 <span data-ttu-id="0c108-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c108-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c108-109">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="0c108-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0c108-110">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c108-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c108-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c108-111">See also</span></span>

- [<span data-ttu-id="0c108-112">IIdentityAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c108-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="0c108-113">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0c108-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
