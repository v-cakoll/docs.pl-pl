---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6bdf56e3d2084dec8d44e1c4d3f0c1e50b711b92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153143"
---
# <a name="issuedtokenparameters"></a>\<issuedTokenParameters >
Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<security>  
\<issuedTokenParameters >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|Określa wersje specyfikacji zabezpieczenia (WS-Security WS-Trust, zabezpieczenia WS konwersacji i polityki WS-Security) muszą być obsługiwane przez wiązanie. Ta wartość jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Określa wymagania dotyczące dołączania tokenu. Ten atrybut jest typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Liczba całkowita określająca rozmiar klucza tokenu. Wartość domyślna to 256.|  
|keyType|Nieprawidłowa wartość <xref:System.IdentityModel.Tokens.SecurityKeyType> , który określa typ klucza. Wartość domyślna to `SymmetricKey`.|  
|tokenType|Ciąg określający typ tokenu. Wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|Kolekcja elementów konfiguracji, które określają dodatkowe parametry żądania.|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Określa kolekcję wymaganych typów oświadczeń.<br /><br /> W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń. Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.|  
|[\<Wystawca >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|Element konfiguracji, który określa punkt końcowy, który wystawia bieżącego tokenu.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|Element konfiguracji, który określa adres punktu końcowego metadanych wystawcy tokenów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Możliwości zabezpieczeń powiązań niestandardowych](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
