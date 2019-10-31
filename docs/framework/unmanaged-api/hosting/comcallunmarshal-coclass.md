---
title: ComCallUnmarshal — Klasa coclass
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
ms.openlocfilehash: 38f3140a181deae1a86569bfc2eb7cf3cd7d1991
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131932"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="e1457-102">ComCallUnmarshal — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="e1457-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="e1457-103">Udostępnia interfejsy służące do zarządzania kierowaniem wskaźników interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e1457-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1457-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1457-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="e1457-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e1457-105">Interfaces</span></span>  
  
|<span data-ttu-id="e1457-106">Interface</span><span class="sxs-lookup"><span data-stu-id="e1457-106">Interface</span></span>|<span data-ttu-id="e1457-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e1457-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="e1457-108">Zapewnia metody tworzenia, inicjowania i zarządzania serwerem proxy w procesie klienta.</span><span class="sxs-lookup"><span data-stu-id="e1457-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1457-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1457-109">Requirements</span></span>  
 <span data-ttu-id="e1457-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1457-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1457-111">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="e1457-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e1457-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e1457-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1457-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1457-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1457-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1457-114">See also</span></span>

- [<span data-ttu-id="e1457-115">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="e1457-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
