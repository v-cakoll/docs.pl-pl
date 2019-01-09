---
title: '&lt;ClientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 3f70a4e6e27507c3820e1b67f49664e538ac736f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145752"
---
# <a name="ltclientcredentialsgt"></a>&lt;ClientCredentials&gt;
Określa poświadczenia używane do uwierzytelniania klienta do usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<clientCredentials>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`supportInteractive`|Wartość logiczna określająca czy interaktywny użytkownik może być włączony do wyboru poświadczeń klienta w czasie wykonywania. Wartość domyślna to `true`.|  
|`type`|Ciąg określający typ tego elementu konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|Określa certyfikat używany do uwierzytelniania klienta do usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest >](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|Określa szyfrowany używany do uwierzytelniania klienta do usługi. Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Określa typ niestandardowy token używany do uwierzytelniania klienta do Secure Token Service (STS). Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<elementu równorzędnego >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Określa bieżące poświadczenia elementów równorzędnych. Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Określa certyfikat używany do uwierzytelniania usługi dla klienta i zapewnia struktury do ustawiania opcji certyfikatów. Ten certyfikat musi być podana poza pasmem z usługi do klienta. Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<Windows >](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Określa poświadczenia Windows. Wartość domyślna to poświadczenia bieżącego wątku. Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|  
  
## <a name="remarks"></a>Uwagi  
 Poświadczenia klienta są używane do uwierzytelniania klienta do usługi w przypadkach, gdy jest wymagane uwierzytelnianie wzajemne. Ta sekcja konfiguracji może również określić usługi certyfikatów w scenariuszach gdzie klienta należy zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)
