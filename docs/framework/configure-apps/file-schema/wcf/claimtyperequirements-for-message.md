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
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;claimTypeRequirements&gt; w &lt;message&gt;
Określa kolekcję wymaganych typów oświadczeń.  
  
 Ta kolekcja jest używana przez usługę do określania wymaganych i opcjonalnych oświadczeń, które muszą być w wystawiony token, którego klient używa do uzyskania dostępu do usługi. Usługa udostępnia wymagane oświadczenia w metadanych, jeśli włączono publikowanie WSDL, ale WCF nie wymaga wystawiony token zawierają typy określonym oświadczenia. Chcesz wymusić wymagane oświadczenia, że typy usług, należy wykonać przy użyciu zasad autoryzacji.  
  
 Na klientach federacyjnego Ta kolekcja zawiera listę wymaganych i opcjonalnych oświadczeń, które są przesyłane do usługi tokenu zabezpieczającego w żądaniu klienta dla wystawiony token.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
