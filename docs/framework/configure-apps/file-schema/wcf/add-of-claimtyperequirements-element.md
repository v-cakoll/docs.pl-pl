---
title: <add> z <claimTypeRequirements> — element
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 47eb9f95fd024b7df24a16781b3d89fe6deb0b8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222188"
---
# <a name="add-of-claimtyperequirements-element"></a>\<Dodaj > z \<claimTypeRequirements > element
Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu. Na przykład usługi stanu wymagania dotyczące poświadczeń przychodzących, które muszą posiadać określone typy oświadczeń.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<wsFederatedBinding>  
\<Powiązanie >  
\<security>  
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
|Typ oświadczenia|Identyfikator URI definiujący typ oświadczenia. Na przykład aby kupić produkt z witryny sieci Web, użytkownik musi przedstawić ważnej karty kredytowej z wystarczającą limit środków. Typ oświadczenia będzie karty kredytowej identyfikatora URI.|  
|isOptional|Wartość logiczna określająca, czy jest to dla opcjonalnego roszczenia. Ustaw ten atrybut na `false` Jeśli jest to wymagane oświadczenia.<br /><br /> Można użyć tego atrybutu, gdy usługa poprosi o podanie pewnych informacji, ale nie jest wymagane. Na przykład jeśli możesz wymagać od użytkownika, wprowadź swoje imię, nazwisko i adres, ale zdecydować, że numer telefonu jest opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Określa kolekcję wymaganych typów oświadczeń. Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń. Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.|  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
