---
title: <add><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920208"
---
# <a name="add-of-claimtyperequirements-element"></a>\<Dodaj > \<elementu claimTypeRequirements >
Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji. Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.  
  
 \<system.ServiceModel>  
\<> powiązań  
\<wsFederatedBinding >  
\<> powiązania  
\<> zabezpieczeń  
\<message>  
\<claimTypeRequirements>  
  
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
|Claim|Identyfikator URI, który definiuje typ żądania. Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym. Typ zgłoszenia to identyfikator URI karty kredytowej.|  
|isoption|Wartość logiczna określająca, czy jest to dla opcjonalnego żądania. Ustaw ten atrybut na `false` , jeśli jest to wymagane żądanie.<br /><br /> Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego. Na przykład, jeśli użytkownik musi wprowadzić imię i nazwisko, nazwisko i adres, ale określić, że numer telefonu jest opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|Określa kolekcję wymaganych typów roszczeń. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń. Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń. Ten wymóg jest zamieszczony w zasadach zabezpieczeń. Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
