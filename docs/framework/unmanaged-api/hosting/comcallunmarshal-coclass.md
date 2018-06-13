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
ms.openlocfilehash: 7884d53630ca13a30d7b4efd55d46684a9dd7d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427645"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="80756-102">ComCallUnmarshal — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="80756-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="80756-103">Zawiera interfejsy zarządzania organizowanie wskaźniki interfejsu.</span><span class="sxs-lookup"><span data-stu-id="80756-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80756-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80756-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="80756-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="80756-105">Interfaces</span></span>  
  
|<span data-ttu-id="80756-106">Interface</span><span class="sxs-lookup"><span data-stu-id="80756-106">Interface</span></span>|<span data-ttu-id="80756-107">Opis</span><span class="sxs-lookup"><span data-stu-id="80756-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="80756-108">Udostępnia metody do tworzenia, inicjowanie i zarządzania serwera proxy w ramach procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="80756-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80756-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80756-109">Requirements</span></span>  
 <span data-ttu-id="80756-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80756-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80756-111">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="80756-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="80756-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80756-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80756-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80756-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80756-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80756-114">See Also</span></span>  
 [<span data-ttu-id="80756-115">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="80756-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
