---
title: <claimTypeRequirements> Aby uzyskać <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 9cf77f6c026df5f78cc8ae6e6783e91f1c86e282
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367456"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="332b3-102">\<claimTypeRequirements > dla \<wiadomości ></span><span class="sxs-lookup"><span data-stu-id="332b3-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="332b3-103">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="332b3-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="332b3-104">Ta kolekcja jest używana przez usługę do określania wymaganych i opcjonalnych oświadczeń, które muszą być w wystawiony token, którego klient używa do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="332b3-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="332b3-105">Usługa udostępnia wymagane oświadczenia w metadanych, jeśli włączono publikowanie WSDL, ale WCF nie wymaga wystawiony token zawierają typy określonym oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="332b3-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="332b3-106">Chcesz wymusić wymagane oświadczenia, że typy usług, należy wykonać przy użyciu zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="332b3-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="332b3-107">Na klientach federacyjnego Ta kolekcja zawiera listę wymaganych i opcjonalnych oświadczeń, które są przesyłane do usługi tokenu zabezpieczającego w żądaniu klienta dla wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="332b3-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332b3-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="332b3-108">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
