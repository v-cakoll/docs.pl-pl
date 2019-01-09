---
title: '&lt;issuerMetadata&gt; w &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 76956c54739219bbde78f378a12d59563ab785c4
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148750"
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a>&lt;issuerMetadata&gt; w &lt;issuedTokenParameters&gt;
\<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<issuedTokenParameters >  
\<issuerMetadata >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Wymagana. Ciąg, który określa adres punktu końcowego. Adres musi być bezwzględnym identyfikatorem URI. Wartością domyślną jest ciąg pusty.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nagłówki >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekcję nagłówków adresowych.|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Możliwości zabezpieczeń powiązań niestandardowych](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
