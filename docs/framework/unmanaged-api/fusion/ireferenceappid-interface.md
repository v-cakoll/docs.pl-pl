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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789691"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="e4061-102">IReferenceAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e4061-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="e4061-103">Reprezentuje odwołanie do Unikatowy identyfikator aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e4061-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4061-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e4061-104">Methods</span></span>  
  
|<span data-ttu-id="e4061-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4061-105">Method</span></span>|<span data-ttu-id="e4061-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e4061-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="e4061-107">Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji odwołuje się ten `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="e4061-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="e4061-108">Ustawia identyfikator kodu dla aplikacji odwołuje się ten `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="e4061-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="e4061-109">Pobiera wskaźnik interfejsu do `IEnumReferenceIdentity` zawierające wystąpienie `IReferenceIdentity` wystąpień, które reprezentują elementy członkowskie tego `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="e4061-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="e4061-110">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla subskrypcji w tym `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="e4061-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="e4061-111">Ustawia token identyfikator subskrypcji to `IReferenceAppId` wartości określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="e4061-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4061-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4061-112">Requirements</span></span>  
 <span data-ttu-id="e4061-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4061-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4061-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e4061-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e4061-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4061-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4061-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4061-116">See also</span></span>

- [<span data-ttu-id="e4061-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="e4061-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="e4061-118">IEnumReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4061-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="e4061-119">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4061-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
