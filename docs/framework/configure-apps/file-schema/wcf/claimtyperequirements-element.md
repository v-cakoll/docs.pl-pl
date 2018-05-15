---
title: '&lt;claimTypeRequirements&gt;, element'
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 3a8bacf4dad2140e3d162cca89c6bd3ecf54b41f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="31b4d-102">&lt;claimTypeRequirements&gt;, element</span><span class="sxs-lookup"><span data-stu-id="31b4d-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="31b4d-103">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="31b4d-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="31b4d-104">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="31b4d-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="31b4d-105">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="31b4d-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="31b4d-106">Każdy element podrzędny w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="31b4d-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="31b4d-107">Wymaganie typów oświadczeń składa się z identyfikatora URI typu oświadczenia wymagane w wystawiony token wraz z parametrem logicznym, która wskazuje, czy oświadczeń typu w wystawiony token jest wymagana lub jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="31b4d-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b4d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31b4d-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="31b4d-109">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="31b4d-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="31b4d-110">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="31b4d-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="31b4d-111">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="31b4d-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="31b4d-112">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="31b4d-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="31b4d-113">\<add></span><span class="sxs-lookup"><span data-stu-id="31b4d-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [<span data-ttu-id="31b4d-114">Powiązania</span><span class="sxs-lookup"><span data-stu-id="31b4d-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="31b4d-115">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="31b4d-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="31b4d-116">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="31b4d-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="31b4d-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="31b4d-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="31b4d-118">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="31b4d-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="31b4d-119">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="31b4d-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
