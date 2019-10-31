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
ms.openlocfilehash: 22a6af61251942f068676daaee2bdfa868e32a97
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134556"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="16a88-102">GetAppIdAuthority — Funkcja</span><span class="sxs-lookup"><span data-stu-id="16a88-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="16a88-103">Pobiera wskaźnik do wystąpienia [IAppIdAuthority —](iappidauthority-interface.md) , które zarządza kluczami dla tożsamości i odwołań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16a88-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16a88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="16a88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16a88-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="16a88-106">określoną Zwrócony wskaźnik `IAppIdAuthority`.</span><span class="sxs-lookup"><span data-stu-id="16a88-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16a88-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16a88-107">Requirements</span></span>  
 <span data-ttu-id="16a88-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16a88-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16a88-109">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="16a88-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="16a88-110">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16a88-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a88-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16a88-111">See also</span></span>

- [<span data-ttu-id="16a88-112">IAppIdAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="16a88-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="16a88-113">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="16a88-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
