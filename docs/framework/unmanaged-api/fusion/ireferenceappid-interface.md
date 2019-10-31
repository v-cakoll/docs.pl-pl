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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131659"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="ef8dd-102">IReferenceAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8dd-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="ef8dd-103">Reprezentuje odwołanie do unikatowego identyfikatora aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ef8dd-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef8dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ef8dd-104">Methods</span></span>  
  
|<span data-ttu-id="ef8dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ef8dd-105">Method</span></span>|<span data-ttu-id="ef8dd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ef8dd-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="ef8dd-107">Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji, do której odwołuje się ten `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ef8dd-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="ef8dd-108">Ustawia identyfikator kodu dla aplikacji, do której odwołuje się ten `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ef8dd-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="ef8dd-109">Pobiera wskaźnik interfejsu do wystąpienia `IEnumReferenceIdentity` zawierającego wystąpienia `IReferenceIdentity`, które reprezentują członków tego `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ef8dd-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="ef8dd-110">Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji tej `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ef8dd-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="ef8dd-111">Ustawia identyfikator tokenu dla subskrypcji tej `IReferenceAppId` na określoną wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="ef8dd-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef8dd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef8dd-112">Requirements</span></span>  
 <span data-ttu-id="ef8dd-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef8dd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8dd-114">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="ef8dd-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ef8dd-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8dd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef8dd-116">See also</span></span>

- [<span data-ttu-id="ef8dd-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="ef8dd-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="ef8dd-118">IEnumReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8dd-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="ef8dd-119">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8dd-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
