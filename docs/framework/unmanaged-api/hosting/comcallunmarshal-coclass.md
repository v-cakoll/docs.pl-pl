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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fde42e3ecfac81a168920bc152833be7ba72b995
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779084"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="e6c29-102">ComCallUnmarshal — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="e6c29-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="e6c29-103">Zawiera interfejsy zarządzania, organizowanie wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e6c29-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6c29-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="e6c29-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e6c29-105">Interfaces</span></span>  
  
|<span data-ttu-id="e6c29-106">Interface</span><span class="sxs-lookup"><span data-stu-id="e6c29-106">Interface</span></span>|<span data-ttu-id="e6c29-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e6c29-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="e6c29-108">Zawiera metody służące do tworzenia, inicjowanie i zarządzania serwera proxy w ramach procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c29-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6c29-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6c29-109">Requirements</span></span>  
 <span data-ttu-id="e6c29-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6c29-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6c29-111">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e6c29-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e6c29-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6c29-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6c29-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6c29-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c29-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6c29-114">See also</span></span>

- [<span data-ttu-id="e6c29-115">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="e6c29-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
