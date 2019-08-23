---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925342"
---
# <a name="issuedtokenparameters"></a>\<issuedTokenParameters >
Określa parametry tokenu zabezpieczającego wydanego w federacyjnym scenariuszu zabezpieczeń.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<> zabezpieczeń  
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
|defaultMessageSecurityVersion|Określa wersje specyfikacji zabezpieczeń (WS-Security, WS-Trust, WS-Secure konwersacja i zasady WS-Security), które muszą być obsługiwane przez powiązanie. Ta wartość jest typu <xref:System.ServiceModel.MessageSecurityVersion>.|  
|Dołączanie|Określa wymagania dotyczące dołączania tokenu. Ten atrybut jest typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Liczba całkowita określająca rozmiar klucza tokenu. Wartość domyślna to 256.|  
|keyType|Prawidłowa wartość <xref:System.IdentityModel.Tokens.SecurityKeyType> określająca typ klucza. Wartość domyślna to `SymmetricKey`.|  
|Obiektu TokenType|Ciąg określający typ tokenu. Wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|Kolekcja elementów konfiguracji, które określają dodatkowe parametry żądania.|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|Określa kolekcję wymaganych typów roszczeń.<br /><br /> W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących. Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń. Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.|  
|[\<> wystawcy](issuer-of-issuedtokenparameters.md)|Element konfiguracji, który określa punkt końcowy, który wystawia bieżący token.|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|Element konfiguracji, który określa adres punktu końcowego metadanych wystawcy tokenu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
|[\<> zabezpieczeń](security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../wcf/samples/custom-binding-security.md)
- [Uwierzytelnianie i tożsamość usług](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Możliwości zabezpieczeń powiązań niestandardowych](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
