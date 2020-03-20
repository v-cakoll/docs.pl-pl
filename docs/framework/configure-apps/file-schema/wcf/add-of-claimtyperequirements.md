---
title: <add> dla <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153090"
---
# <a name="add-of-claimtyperequirements"></a>\<dodawanie> wymagań \<dotyczących typu oświadczeń>
Określa typy wymaganych i opcjonalnych oświadczeń, które mają pojawić się w poświadczeniu federacyjnem. Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą zawierać określony zestaw typów oświadczeń.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>niestandardowe**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>bezpieczeństwa**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wydaneTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimType Wymagania>**](claimtyperequirements-element.md)\
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
|[\<claimType Wymagania>](claimtyperequirements-element.md)|Określa kolekcję wymaganych typów oświadczeń.<br /><br /> W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń. Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń oczekuje się, że pojawią się w poświadczeniu federacyjne.|  
  
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

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimType Wymagania>](claimtyperequirements-element.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<>niestandardowe](custombinding.md)
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../wcf/samples/custom-binding-security.md)
