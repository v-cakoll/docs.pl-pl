---
title: '&lt;add&gt; w &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752458"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;add&gt; w &lt;issuerChannelBehaviors&gt;
Dodaje zachowanie punktu końcowego, który będzie używany podczas komunikacji z STS.  
  
> [!NOTE]
>  Jeśli jakiekolwiek zachowanie punktu końcowego zawiera [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, zostanie wygenerowany wyjątek.  
  
 \<system.ServiceModel>  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials>  
\<issuedToken >  
\<issuerChannelBehaviors > — Element  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|issuerAddress|Identyfikator URI do komunikacji z wystawcą tokenu zabezpieczenia.|  
|behaviorConfiguration|Nazwa zachowania punktu końcowego zdefiniowana w pliku konfiguracyjnym.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Zawiera kolekcję zachowania punktu końcowego klienta Windows Communication Foundation (WCF) używanego podczas komunikacji z określonych usług tokenu usługi.|  
  
## <a name="remarks"></a>Uwagi  
 `issuerAddress` zawiera identyfikator URI usługi tokenu zabezpieczającego, który klient do komunikacji z. `behaviorConfiguration` Wskazuje zachowanie punktu końcowego, w której aplikacja będzie używać w kanałach utworzony przez Windows Communication Foundation (WCF) można pobrać wystawionych tokenów z usługi tokenu zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Instrukcje: konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
