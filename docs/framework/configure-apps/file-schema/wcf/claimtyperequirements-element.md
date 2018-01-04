---
title: '&lt;claimTypeRequirements&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea3b62620788d108f9b2a35c94dab8ddc6463ada
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="1065f-102">&lt;claimTypeRequirements&gt;, element</span><span class="sxs-lookup"><span data-stu-id="1065f-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="1065f-103">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1065f-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="1065f-104">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1065f-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1065f-105">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1065f-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1065f-106">Każdy element podrzędny w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="1065f-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="1065f-107">Wymaganie typów oświadczeń składa się z identyfikatora URI typu oświadczenia wymagane w wystawiony token wraz z parametrem logicznym, która wskazuje, czy oświadczeń typu w wystawiony token jest wymagana lub jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1065f-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1065f-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1065f-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1065f-109">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="1065f-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1065f-110">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="1065f-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1065f-111">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="1065f-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="1065f-112">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="1065f-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1065f-113">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="1065f-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [<span data-ttu-id="1065f-114">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1065f-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1065f-115">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1065f-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1065f-116">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1065f-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1065f-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1065f-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="1065f-118">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1065f-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="1065f-119">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1065f-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
