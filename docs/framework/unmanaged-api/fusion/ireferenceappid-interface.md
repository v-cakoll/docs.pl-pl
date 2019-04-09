---
title: IReferenceAppId — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157199"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="62fb7-102">IReferenceAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62fb7-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="62fb7-103">Reprezentuje odwołanie do Unikatowy identyfikator aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="62fb7-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62fb7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="62fb7-104">Methods</span></span>  
  
|<span data-ttu-id="62fb7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="62fb7-105">Method</span></span>|<span data-ttu-id="62fb7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="62fb7-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="62fb7-107">Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji odwołuje się ten `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62fb7-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="62fb7-108">Ustawia identyfikator kodu dla aplikacji odwołuje się ten `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62fb7-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="62fb7-109">Pobiera wskaźnik interfejsu do `IEnumReferenceIdentity` zawierające wystąpienie `IReferenceIdentity` wystąpień, które reprezentują elementy członkowskie tego `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62fb7-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="62fb7-110">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla subskrypcji w tym `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62fb7-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="62fb7-111">Ustawia token identyfikator subskrypcji to `IReferenceAppId` wartości określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="62fb7-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62fb7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62fb7-112">Requirements</span></span>  
 <span data-ttu-id="62fb7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62fb7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62fb7-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="62fb7-114">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="62fb7-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="62fb7-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62fb7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62fb7-116">See also</span></span>

- [<span data-ttu-id="62fb7-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="62fb7-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="62fb7-118">IEnumReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62fb7-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="62fb7-119">IReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62fb7-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
