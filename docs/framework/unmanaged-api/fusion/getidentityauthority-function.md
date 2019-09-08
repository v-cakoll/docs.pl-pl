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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f29246bdb929c8eaf1ebce726164d5cd2269b9f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796861"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="1dc54-102">GetIdentityAuthority — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1dc54-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="1dc54-103">Pobiera wskaźnik do wystąpienia [IIdentityAuthority —](iidentityauthority-interface.md) , które zarządza kluczami obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="1dc54-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dc54-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dc54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dc54-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="1dc54-106">określoną Zwrócony `IIdentityAuthority` wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="1dc54-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc54-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dc54-107">Requirements</span></span>  
 <span data-ttu-id="1dc54-108">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dc54-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc54-109">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="1dc54-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1dc54-110">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc54-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc54-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dc54-111">See also</span></span>

- [<span data-ttu-id="1dc54-112">IIdentityAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="1dc54-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="1dc54-113">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="1dc54-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
