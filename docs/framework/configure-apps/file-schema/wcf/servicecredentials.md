---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 54ac4f0aa31a4311976449d545880d825c06337d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256475"
---
# <a name="servicecredentials"></a>\<serviceCredentials>
Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`type`|Ciąg określający typ tego elementu konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępne poza pasmem. Ten element określa również ustawienia weryfikacji certyfikatu klienta. Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Określa bieżący token wystawiony dla tej usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.|  
|[\<elementu równorzędnego >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Określa bieżące poświadczenia dla węzła równorzędnego. Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<secureConversationAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|Określa bieżące poświadczenia dla bezpiecznej konwersacji. Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Określa certyfikat używany przez usługę do identyfikacji. Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.|  
|[\<userNameAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|Określa ustawienia dla sprawdzenie poprawności hasła nazwy użytkownika. Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.|  
|[\<windowsAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|Określa ustawienia dla sprawdzanie poprawności poświadczeń Windows. Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
