---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9a8d701e0806aae0a17a1c5ff7284606dd080f85
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750236"
---
# <a name="ltissuedtokengt"></a>&lt;IssuedToken&gt;
Określa niestandardowy token używany do uwierzytelniania klienta do usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials>  
\<issuedToken >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Opcjonalny logiczny atrybut, który określa, czy tokeny są buforowane. Wartość domyślna to `true`.|  
|`defaultKeyEntropyMode`|Atrybut opcjonalny ciąg, który określa, które losowe wartości (entropie) są używane dla operacji uzgadniania. Wartości to `ClientEntropy`, `ServerEntropy`, i `CombinedEntropy`, wartość domyślna to `CombinedEntropy`. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Atrybut opcjonalny całkowity, który określa procent prawidłowego przedziału czasowego (dostarczonych przez emitenta tokenu) jaki może upłynąć, zanim token jest odnawiany. Są wartości z zakresu od 0 do 100. Wartość domyślna to 60, który określa 60% upływu czasu, przed podjęciem próby odnowienia.|  
|`issuerChannelBehaviors`|Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z wystawcą.|  
|`localIssuerChannelBehaviors`|Opcjonalny atrybut, który określa zachowania kanału do użycia przy komunikacji z lokalnym wystawcą.|  
|`maxIssuedTokenCachingTime`|Opcjonalny atrybut Timespan określający okres czasu, który wystawił tokeny są buforowane, gdy emitent tokenów (STS) określił czasu. Wartość domyślna to "10675199.02:48:05.4775807."|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Określa adres wystawcy lokalnego token i powiązania, używany do komunikacji z punktem końcowym.|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Określa zachowania punktu końcowego do użycia podczas nawiązywania kontaktu wystawcy lokalnego.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Wystawiony token jest typu niestandardowego poświadczenia używane, na przykład podczas uwierzytelniania z Secure Token Service (STS) w federacyjnym scenariuszu. Domyślnie token jest tokenu SAML. Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). i [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Ta sekcja zawiera elementy umożliwia konfigurowanie lokalnego wystawcy tokenów lub zachowania używane z usługi tokenu zabezpieczającego. Aby uzyskać instrukcje dotyczące konfigurowania klienta do używania wystawcy lokalnego, zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Instrukcje: konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
