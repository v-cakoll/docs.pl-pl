---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 2910f47b85ee67694cae0c3a725c3c7c7b3803c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701726"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="22197-101">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="22197-101">\<authorizationPolicies></span></span>
<span data-ttu-id="22197-102">Ta sekcja konfiguracji zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="22197-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="22197-103">Zasady autoryzacji, każdy zawiera jeden wymagane `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="22197-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="22197-104">Ten atrybut określa zasady autoryzacji, która umożliwia przekształcanie jednego zestawu oświadczeń wejściowych na inny zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="22197-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="22197-105">Udzielić lub odmówić kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="22197-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="22197-106">Aby uzyskać więcej informacji na temat sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="22197-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22197-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22197-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="22197-108">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="22197-108">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="22197-109">Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="22197-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="22197-110">\<add></span><span class="sxs-lookup"><span data-stu-id="22197-110">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="22197-111">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="22197-111">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
