---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926461"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="b4c17-101">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="b4c17-101">\<authorizationPolicies></span></span>
<span data-ttu-id="b4c17-102">Ta sekcja konfiguracji zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="b4c17-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="b4c17-103">Każda zasada autoryzacji zawiera jeden wymagany `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="b4c17-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="b4c17-104">Ten atrybut określa zasady autoryzacji, które umożliwiają przekształcanie jednego zestawu oświadczeń wejściowych w inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="b4c17-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="b4c17-105">Na podstawie tego można udzielić lub odmówić kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="b4c17-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="b4c17-106">Aby uzyskać więcej informacji na temat działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="b4c17-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c17-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4c17-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="b4c17-108">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="b4c17-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="b4c17-109">Instrukcje: Tworzenie niestandardowego Menedżera autoryzacji dla usługi</span><span class="sxs-lookup"><span data-stu-id="b4c17-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="b4c17-110">\<add></span><span class="sxs-lookup"><span data-stu-id="b4c17-110">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="b4c17-111">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="b4c17-111">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
