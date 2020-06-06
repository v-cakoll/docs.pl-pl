---
title: <claimTypeRequirements>, element
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926146"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="0da21-102">\<claimTypeRequirements>, element</span><span class="sxs-lookup"><span data-stu-id="0da21-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="0da21-103">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="0da21-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="0da21-104">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="0da21-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="0da21-105">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="0da21-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="0da21-106">Każdy element podrzędny w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="0da21-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="0da21-107">Wymaganie typu dla żądania składa się z identyfikatora URI typu zgłoszenia żądanego w wystawionym tokenie oraz parametru logicznego, który wskazuje, czy ten typ zgłoszenia jest wymagany w wystawionym tokenie, czy jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0da21-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da21-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0da21-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0da21-109">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="0da21-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0da21-110">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0da21-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0da21-111">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="0da21-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0da21-112">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0da21-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="0da21-113">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0da21-113">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0da21-114">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="0da21-114">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0da21-115">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0da21-115">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="0da21-116">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0da21-116">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="0da21-117">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="0da21-117">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
