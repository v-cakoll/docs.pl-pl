---
title: "IReferenceAppId — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="c4c2b-102">IReferenceAppId — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c4c2b-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="c4c2b-103">Reprezentuje odwołanie do Unikatowy identyfikator dla aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c4c2b-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4c2b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4c2b-104">Methods</span></span>  
  
|<span data-ttu-id="c4c2b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4c2b-105">Method</span></span>|<span data-ttu-id="c4c2b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c4c2b-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="c4c2b-107">Pobiera wskaźnik do reprezentacji ciągu identyfikatora kodu dla aplikacji odwołuje się to `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c4c2b-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="c4c2b-108">Określa identyfikator kodu dla aplikacji odwołuje się to `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c4c2b-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="c4c2b-109">Pobiera wskaźnika interfejsu do `IEnumReferenceIdentity` zawierające wystąpienie `IReferenceIdentity` wystąpień, które reprezentują członkami to `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c4c2b-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="c4c2b-110">Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla tej subskrypcji `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c4c2b-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="c4c2b-111">Ustawia token identyfikator subskrypcji do tego `IReferenceAppId` wartości określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="c4c2b-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4c2b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4c2b-112">Requirements</span></span>  
 <span data-ttu-id="c4c2b-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4c2b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c2b-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c4c2b-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c4c2b-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c2b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c2b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4c2b-116">See Also</span></span>  
 [<span data-ttu-id="c4c2b-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="c4c2b-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="c4c2b-118">IEnumReferenceIdentity — interfejs</span><span class="sxs-lookup"><span data-stu-id="c4c2b-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="c4c2b-119">IReferenceIdentity — interfejs</span><span class="sxs-lookup"><span data-stu-id="c4c2b-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
