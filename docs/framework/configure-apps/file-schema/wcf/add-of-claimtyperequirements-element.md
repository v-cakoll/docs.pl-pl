---
title: '&lt;add&gt; w &lt;claimTypeRequirements&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a6a0cc78cad2ccbc8dca6097227ef22f45dbc63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a>&lt;add&gt; w &lt;claimTypeRequirements&gt;, element
Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu. Na przykład usługi stanu wymagania dotyczące poświadczeń przychodzących, które muszą posiadać określone typy oświadczeń.  
  
 \<System. ServiceModel >  
\<powiązania >  
\<wsFederatedBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<komunikat >  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Typ oświadczenia|Identyfikator URI definiujący typ oświadczenia. Na przykład aby kupić produktu w witrynie sieci Web, użytkownik musi przedstawić ważnej karty kredytowej z limitem kredytu wystarczające. Typ oświadczenia będą karty kredytowej identyfikatora URI.|  
|isOptional|Wartość logiczna określająca, czy jest to dla opcjonalnego roszczenia. Ten atrybut na `false` Jeśli jest to wymagane oświadczenia.<br /><br /> Można użyć tego atrybutu, gdy usługa wprowadza pewne informacje, ale nie jest wymagane. Na przykład jeśli wymagają od użytkownika wprowadzenia jego imię, nazwisko i adres, ale zdecydować, czy numer telefonu jest opcjonalne.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Określa kolekcję wymaganych typów oświadczeń. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń. Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń. To wymaganie jest dyskowe widoczne w zasadach zabezpieczeń. Gdy klient żądania poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagań do żądania tokenu (RequestSecurityToken) tak, aby usługi federacyjnej można wydać poświadczenia, które spełniają wymagania odpowiednio.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja dodaje dwa wymagania typu oświadczenia do powiązania zabezpieczeń.  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
