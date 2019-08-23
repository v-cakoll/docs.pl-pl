---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936295"
---
# <a name="servicecredentials"></a>\<serviceCredentials>
Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
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
|[\<> clientCertificate](clientcertificate-of-servicecredentials.md)|Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępny poza pasmem. Ten element określa również ustawienia weryfikacji certyfikatu klienta. Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.|  
|[\<issuedTokenAuthentication >](issuedtokenauthentication-of-servicecredentials.md)|Określa bieżący token wystawiony dla tej usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.|  
|[\<> elementów równorzędnych](peer-of-servicecredentials.md)|Określa bieżące poświadczenia dla węzła równorzędnego. Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|Określa bieżące poświadczenia dla bezpiecznej konwersacji. Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.|  
|[\<> serviceCertificate](servicecertificate-of-servicecredentials.md)|Określa certyfikat używany przez usługę do zidentyfikowania siebie. Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.|  
|[\<userNameAuthentication>](usernameauthentication.md)|Określa ustawienia dla walidacji hasła użytkownika. Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement>.|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|Określa ustawienia weryfikacji poświadczeń systemu Windows. Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
