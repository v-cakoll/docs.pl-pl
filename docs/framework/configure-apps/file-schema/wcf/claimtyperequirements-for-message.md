---
title: '&lt;claimTypeRequirements&gt; w &lt;message&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 747ac641f8602010819baa00033f3663e2e5f678
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="8bb83-102">&lt;claimTypeRequirements&gt; w &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="8bb83-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="8bb83-103">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8bb83-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="8bb83-104">Kolekcja jest używana przez usługę do określania wymaganych i opcjonalnych oświadczeń, które muszą być w wystawionego tokenu, którego klient używa do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb83-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="8bb83-105">Usługa przedstawia wymaganych typów oświadczeń w metadanych, jeśli publikowanie WSDL jest włączona, ale WCF nie wymaga wystawiony token zawiera typy określone oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="8bb83-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="8bb83-106">Usługi chcą wymusić typy są obecne wymagane oświadczeń należy wykonać przy użyciu zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="8bb83-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="8bb83-107">Na klientach federacyjnych Ta kolekcja zawiera listę wymaganych i opcjonalnych oświadczeń, które są przesyłane do usługi tokenu zabezpieczającego w żądaniu klienta dla wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="8bb83-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb83-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb83-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
