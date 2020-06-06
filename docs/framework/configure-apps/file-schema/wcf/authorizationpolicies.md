---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926461"
---
# \<authorizationPolicies>
<span data-ttu-id="a7624-101">Ta sekcja konfiguracji zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a7624-101">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="a7624-102">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="a7624-102">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="a7624-103">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="a7624-103">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="a7624-104">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="a7624-104">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="a7624-105">Aby uzyskać więcej informacji na temat działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="a7624-105">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7624-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7624-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="a7624-107">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="a7624-107">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="a7624-108">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="a7624-108">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="a7624-109">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="a7624-109">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
