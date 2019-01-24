---
title: '&lt;claimTypeRequirements&gt; w &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 5c2bc05887701e78335629a37ce82815ac9abda5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628871"
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="152fb-102">&lt;claimTypeRequirements&gt; w &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="152fb-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="152fb-103">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="152fb-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="152fb-104">Ta kolekcja jest używana przez usługę do określania wymaganych i opcjonalnych oświadczeń, które muszą być w wystawiony token, którego klient używa do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="152fb-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="152fb-105">Usługa udostępnia wymagane oświadczenia w metadanych, jeśli włączono publikowanie WSDL, ale WCF nie wymaga wystawiony token zawierają typy określonym oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="152fb-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="152fb-106">Chcesz wymusić wymagane oświadczenia, że typy usług, należy wykonać przy użyciu zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="152fb-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="152fb-107">Na klientach federacyjnego Ta kolekcja zawiera listę wymaganych i opcjonalnych oświadczeń, które są przesyłane do usługi tokenu zabezpieczającego w żądaniu klienta dla wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="152fb-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152fb-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="152fb-108">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
