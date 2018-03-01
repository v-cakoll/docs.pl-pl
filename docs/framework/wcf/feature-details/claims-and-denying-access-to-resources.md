---
title: "Oświadczenia i odmawianie dostępu do zasobów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 156856ddd1a4c3b1d8f77a8a61f7e0336f993839
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="e853e-102">Oświadczenia i odmawianie dostępu do zasobów</span><span class="sxs-lookup"><span data-stu-id="e853e-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e853e-103">obsługuje mechanizm autoryzacji opartej na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="e853e-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="e853e-104">A także zezwalanie na dostęp do zasobów na podstawie obecności oświadczenia, systemów często odmówić dostępu do zasobów na podstawie obecności oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="e853e-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="e853e-105">Należy zbadać takich systemów <xref:System.IdentityModel.Policy.AuthorizationContext> oświadczeń, które powodują powstanie dostępu przed wyszukiwanie oświadczeń, których wynikiem jest dozwolony dostęp do.</span><span class="sxs-lookup"><span data-stu-id="e853e-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="e853e-106">Na przykład system może być odmowa dostępu do zasobu dla każdego, kto ma oświadczenie o typie z `Age`, prawej strony <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i wartości zasobów `Under 21` tylko po jego tożsamość ma również oświadczenie typu `Name`, po prawej <xref:System.IdentityModel.Claims.Rights.Identity%2A>, i wartości zasobów `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="e853e-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="e853e-107">Innymi słowy, systemu nie zezwala na dostęp do każdego, kto jest 21 roku życia i nieograniczony dostęp, gdy nazwa Mallory.</span><span class="sxs-lookup"><span data-stu-id="e853e-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="e853e-108">Aby prawidłowo zaimplementować to semantyczne, ważne jest, aby wyszukać `Age` oświadczeń najpierw oraz określają, czy w obszarze 21 lat ważności.</span><span class="sxs-lookup"><span data-stu-id="e853e-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="e853e-109">W przeciwnym razie, jeśli Mallory znajduje się w obszarze 21, następnie zasobu może otrzymać dostęp wyłącznie w oparciu o `Name` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="e853e-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e853e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e853e-110">See Also</span></span>  
 [<span data-ttu-id="e853e-111">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="e853e-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="e853e-112">Oświadczenia i tokeny</span><span class="sxs-lookup"><span data-stu-id="e853e-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
