---
title: <issuerMetadata> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: e46e56c6285af24941a550b2c4f7dec3b441db69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214809"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a>\<issuerMetadata > z \<issuedTokenParameters >
\<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<security>  
\<issuedTokenParameters >  
\<issuerMetadata>  
  
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
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekcję nagłówków adresowych.|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Możliwości zabezpieczeń wiązań niestandardowych](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia wiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
