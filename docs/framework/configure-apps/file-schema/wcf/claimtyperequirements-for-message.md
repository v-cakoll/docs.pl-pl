---
title: <claimTypeRequirements>dla<message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: db6717022bf3af0c4922818668595dd3937e9c71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704410"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="8db1a-102">\<claimTypeRequirements>dla\<message></span><span class="sxs-lookup"><span data-stu-id="8db1a-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="8db1a-103">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="8db1a-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="8db1a-104">Kolekcja jest używana przez usługę do określenia wymaganych i opcjonalnych oświadczeń, które muszą znajdować się w wystawionym tokenie używanym przez klienta w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="8db1a-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="8db1a-105">Usługa uwidacznia wymagane typy roszczeń w metadanych, jeśli jest włączona funkcja publikowania WSDL, ale program WCF nie wymaga, aby wystawiony token zawierał określone typy roszczeń.</span><span class="sxs-lookup"><span data-stu-id="8db1a-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="8db1a-106">Usługi, które chcą wymusić wymagane typy zgłoszeń, powinny używać zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="8db1a-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="8db1a-107">W przypadku klientów federacyjnych ta kolekcja zawiera listę wymaganych i opcjonalnych oświadczeń, które są wysyłane do usługi tokenu zabezpieczającego w żądaniu klienta dla wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="8db1a-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db1a-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8db1a-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
