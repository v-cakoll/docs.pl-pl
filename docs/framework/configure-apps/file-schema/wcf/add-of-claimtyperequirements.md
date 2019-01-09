---
title: '&lt;add&gt; w &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 5d4f0cd71ab9bf69921704300018207c9f7af107
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145214"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a>&lt;add&gt; w &lt;claimTypeRequirements&gt;
Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu. Na przykład usługi stanu wymagania dotyczące poświadczeń przychodzących, które muszą posiadać określone typy oświadczeń.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<issuedTokenParameters >  
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
|Typ oświadczenia|Identyfikator URI definiujący typ oświadczenia. Na przykład aby kupić produkt z witryny sieci Web, użytkownik musi przedstawić ważnej karty kredytowej z wystarczającą limit środków. Typ oświadczenia będzie karty kredytowej identyfikatora URI.|  
|isOptional|Wartość logiczna określająca, czy jest to dla opcjonalnego roszczenia. Ustaw ten atrybut na `false` Jeśli jest to wymagane oświadczenia.<br /><br /> Można użyć tego atrybutu, gdy usługa poprosi o podanie pewnych informacji, ale nie jest wymagane. Na przykład jeśli możesz wymagać od użytkownika, wprowadź swoje imię, nazwisko i adres, ale zdecydować, że numer telefonu jest opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Określa kolekcję wymaganych typów oświadczeń.<br /><br /> W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń. Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń. To wymaganie jest manifestowany w zasadach zabezpieczeń. Jeśli poświadczenia żądania klienta z usługi federacyjnej (na przykład CardSpace), umieszcza je wymagań do żądania tokenu (elemencie RequestSecurityToken) tak, aby usługi federacyjnej może wystawiać poświadczenia, które spełniają wymogi odpowiednio.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja dodaje dwa wymagania dotyczące typu oświadczenia do powiązania zabezpieczeń.  
  
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
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
