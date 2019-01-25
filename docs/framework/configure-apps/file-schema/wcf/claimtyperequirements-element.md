---
title: '&lt;claimTypeRequirements&gt;, element'
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 32eafa3ce235b2087012bd5810a685ad5276e09d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632897"
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="d7f6a-102">&lt;claimTypeRequirements&gt;, element</span><span class="sxs-lookup"><span data-stu-id="d7f6a-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="d7f6a-103">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d7f6a-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="d7f6a-104">W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="d7f6a-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d7f6a-105">Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d7f6a-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d7f6a-106">Każdy element podrzędny w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="d7f6a-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="d7f6a-107">Wymagania dotyczące typu oświadczenia składa się z identyfikatora URI typu oświadczenia wymagane w wystawiony token wraz z parametrem logicznym, która wskazuje, czy oświadczeń typu w wystawiony token jest wymagana lub jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d7f6a-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f6a-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7f6a-108">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d7f6a-109">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="d7f6a-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d7f6a-110">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="d7f6a-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d7f6a-111">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d7f6a-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d7f6a-112">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="d7f6a-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d7f6a-113">\<add></span><span class="sxs-lookup"><span data-stu-id="d7f6a-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)
- [<span data-ttu-id="d7f6a-114">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d7f6a-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d7f6a-115">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="d7f6a-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d7f6a-116">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d7f6a-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d7f6a-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d7f6a-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="d7f6a-118">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d7f6a-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="d7f6a-119">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d7f6a-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
