---
title: <serviceCertificate> z <clientCredentials> — Element
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4fe196ef8737c7abde939e36c2bb7afd5a0d86b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145343"
---
# <a name="servicecertificate-of-clientcredentials-element"></a>\<serviceCertificate > z \<clientCredentials > Element
Określa certyfikat używany podczas uwierzytelniania usługi dla klienta.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<clientCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<defaultCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|Określa certyfikat X.509, który ma być używany gdy usługa lub STS nie zapewnia go poprzez protokół negocjacji.|  
|[\<scopedCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania. Ta kolekcja jest zazwyczaj pozwala ustalić certyfikaty usługi usługi tokenu zabezpieczeń w federacyjnym scenariuszu.|  
|[\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|Określa zachowania uwierzytelnienia dla certyfikatów usługi używanych przez klienta.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane przez klienta do samodzielnego uwierzytelnienia usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji określa ustawienia używane przez klienta, aby zweryfikować certyfikat przedstawiony przez usługę za pomocą uwierzytelniania protokołu SSL. Zawiera ona także dowolny certyfikat dla usługi, która jest jawnie skonfigurowany na komputerze klienckim na potrzeby szyfrowania wiadomości w usłudze korzystanie z zabezpieczeń komunikatów.  
  
 Atrybuty `serviceCertificate` elementu są takie same atrybuty [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpieczanie klientów [WCF]](../../../../../docs/framework/wcf/securing-clients.md)
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
