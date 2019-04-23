---
title: <issuer> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113545"
---
# <a name="issuer-of-issuedtokenparameters"></a>\<Wystawca > z \<issuedTokenParameters >
Określa Usługa tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<security>  
\<issuedTokenParameters >  
\<issuer>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Wymagany ciąg. Adres URL usługi STS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekcja nagłówków adresowych dla punktów końcowych, które można utworzyć konstruktora.|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Podczas używania tokenu wystawionego, określa ustawienia, które umożliwiają klienta do uwierzytelniania serwera.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Określa bieżący wystawiony token.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Możliwości zabezpieczeń powiązań niestandardowych](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
