---
title: <claimTypeRequirements>, element
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926146"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="9095a-102">\<claimTypeRequirements, element ></span><span class="sxs-lookup"><span data-stu-id="9095a-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="9095a-103">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="9095a-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="9095a-104">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9095a-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9095a-105">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="9095a-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9095a-106">Każdy element podrzędny w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="9095a-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="9095a-107">Wymaganie typu dla żądania składa się z identyfikatora URI typu zgłoszenia żądanego w wystawionym tokenie oraz parametru logicznego, który wskazuje, czy ten typ zgłoszenia jest wymagany w wystawionym tokenie, czy jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9095a-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9095a-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9095a-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9095a-109">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="9095a-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9095a-110">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="9095a-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9095a-111">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="9095a-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9095a-112">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="9095a-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9095a-113">\<add></span><span class="sxs-lookup"><span data-stu-id="9095a-113">\<add></span></span>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="9095a-114">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9095a-114">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9095a-115">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9095a-115">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9095a-116">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9095a-116">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9095a-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9095a-117">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="9095a-118">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9095a-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="9095a-119">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="9095a-119">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
