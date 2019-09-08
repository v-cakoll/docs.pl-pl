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
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796369"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="62ff4-102">IReferenceAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62ff4-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="62ff4-103">Reprezentuje odwołanie do unikatowego identyfikatora aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="62ff4-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62ff4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="62ff4-104">Methods</span></span>  
  
|<span data-ttu-id="62ff4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="62ff4-105">Method</span></span>|<span data-ttu-id="62ff4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="62ff4-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="62ff4-107">Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji, do której się odwołuje `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62ff4-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="62ff4-108">Ustawia identyfikator kodu dla aplikacji, do której się odwołuje `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62ff4-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="62ff4-109">Pobiera wskaźnik interfejsu do `IEnumReferenceIdentity` wystąpienia `IReferenceIdentity` zawierającego wystąpienia, które reprezentują elementy członkowskie tego `IReferenceAppId`elementu.</span><span class="sxs-lookup"><span data-stu-id="62ff4-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="62ff4-110">Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="62ff4-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="62ff4-111">Ustawia identyfikator tokenu dla subskrypcji `IReferenceAppId` na wartość określonej wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="62ff4-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62ff4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62ff4-112">Requirements</span></span>  
 <span data-ttu-id="62ff4-113">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ff4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ff4-114">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="62ff4-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="62ff4-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ff4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ff4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62ff4-116">See also</span></span>

- [<span data-ttu-id="62ff4-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="62ff4-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="62ff4-118">IEnumReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="62ff4-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="62ff4-119">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="62ff4-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
