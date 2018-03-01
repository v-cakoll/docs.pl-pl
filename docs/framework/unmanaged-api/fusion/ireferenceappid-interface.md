---
title: "IReferenceAppId — Interfejs"
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
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="687d5-102">IReferenceAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="687d5-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="687d5-103">Reprezentuje odwołanie do Unikatowy identyfikator dla aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="687d5-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="687d5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="687d5-104">Methods</span></span>  
  
|<span data-ttu-id="687d5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="687d5-105">Method</span></span>|<span data-ttu-id="687d5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="687d5-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="687d5-107">Pobiera wskaźnik do reprezentacji ciągu identyfikatora kodu dla aplikacji odwołuje się to `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="687d5-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="687d5-108">Określa identyfikator kodu dla aplikacji odwołuje się to `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="687d5-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="687d5-109">Pobiera wskaźnika interfejsu do `IEnumReferenceIdentity` zawierające wystąpienie `IReferenceIdentity` wystąpień, które reprezentują członkami to `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="687d5-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="687d5-110">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla tej subskrypcji `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="687d5-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="687d5-111">Ustawia token identyfikator subskrypcji do tego `IReferenceAppId` wartości określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="687d5-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="687d5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="687d5-112">Requirements</span></span>  
 <span data-ttu-id="687d5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="687d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="687d5-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="687d5-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="687d5-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="687d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="687d5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="687d5-116">See Also</span></span>  
 [<span data-ttu-id="687d5-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="687d5-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="687d5-118">IEnumReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="687d5-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="687d5-119">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="687d5-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
