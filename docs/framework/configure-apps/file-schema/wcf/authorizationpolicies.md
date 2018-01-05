---
title: '&lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e33dca28f11b564f622ff1c202827c693f0874c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltauthorizationpoliciesgt"></a><span data-ttu-id="99b0b-102">&lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="99b0b-102">&lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="99b0b-103">Ta sekcja konfiguracji zawiera kolekcję typów zasad autoryzacji, które można dodać za pomocą `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="99b0b-103">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="99b0b-104">Każdej zasady autoryzacji zawiera jeden z wymaganych `policyType` atrybut, który jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="99b0b-104">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="99b0b-105">Ten atrybut określa zasady autoryzacji, dzięki czemu przekształcania jednego zestawu oświadczeń wejściowych do innego zestawu oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="99b0b-105">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="99b0b-106">Udzielono lub odmówiono kontrola dostępu oparta na.</span><span class="sxs-lookup"><span data-stu-id="99b0b-106">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="99b0b-107">Aby uzyskać więcej informacji dotyczących sposobu działania zasad autoryzacji, zobacz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i [zasady autoryzacji](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="99b0b-107">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b0b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99b0b-108">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="99b0b-109">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="99b0b-109">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="99b0b-110">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="99b0b-110">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="99b0b-111">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="99b0b-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="99b0b-112">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="99b0b-112">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
