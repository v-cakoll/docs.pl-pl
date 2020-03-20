---
title: <add>element <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153103"
---
# <a name="add-of-claimtyperequirements-element"></a>\<dodawanie> wymagań \<dotyczących typu oświadczeń> element
Określa typy wymaganych i opcjonalnych oświadczeń, które mają pojawić się w poświadczeniu federacyjnem. Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą zawierać określony zestaw typów oświadczeń.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationhttpbinowanie>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>bezpieczeństwa**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>wiadomości**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimType Wymagania>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**
  
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
|Claimtype|Identyfikator URI, który definiuje typ oświadczenia. Na przykład, aby kupić produkt w witrynie sieci Web, użytkownik musi przedstawić prawidłową kartę kredytową z wystarczającym limitem kredytowym. Typ oświadczenia będzie identyfikatorem URI karty kredytowej.|  
|isOprocjonalny|Wartość logiczna, która określa, czy jest to dla opcjonalnego oświadczenia. Ustaw ten atrybut, `false` jeśli jest to wymagane oświadczenie.<br /><br /> Tego atrybutu można użyć, gdy usługa prosi o pewne informacje, ale nie wymaga go. Jeśli na przykład użytkownik wymaga wprowadzenia imienia, nazwiska i adresu, ale zdecyduj, że numer telefonu jest opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimType Wymagania>](claimtyperequirements-for-message.md)|Określa kolekcję wymaganych typów oświadczeń. Każdy element jest <xref:System.ServiceModel.Configuration.ClaimTypeElement>typu .<br /><br /> W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń. Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń oczekuje się, że pojawią się w poświadczeniu federacyjne.|  
  
## <a name="remarks"></a>Uwagi  
 W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń. To wymaganie przejawia się w zasadach zabezpieczeń. Gdy klient żąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), dzięki czemu usługa federacyjne może wystawiać poświadczenia, które spełniają odpowiednio wymagania.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja dodaje dwa wymagania typu oświadczenia do powiązania zabezpieczeń.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
