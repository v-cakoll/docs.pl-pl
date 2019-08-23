---
title: <serviceCertificate><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936340"
---
# <a name="servicecertificate-of-clientcredentials-element"></a>\<> serviceCertificate obiektu \<ClientCredentials > elementu
Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<clientCredentials>  
\<> serviceCertificate  
  
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
|[\<defaultCertificate>](defaultcertificate-element.md)|Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.|  
|[\<scopedCertificates >](scopedcertificates-element.md)|Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania. Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.|  
|[\<> uwierzytelniania](authentication-of-servicecertificate-element.md)|Określa zachowania uwierzytelniania dla certyfikatów usługi używanych przez klienta programu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Określa poświadczenia używane przez klienta do samodzielnego uwierzytelnienia w usłudze.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji określa ustawienia używane przez klienta do weryfikowania certyfikatu przedstawionego przez usługę przy użyciu uwierzytelniania SSL. Zawiera również certyfikat dla usługi, która jest jawnie skonfigurowana na kliencie do szyfrowania komunikatów w usłudze przy użyciu zabezpieczeń komunikatów.  
  
 Atrybuty `serviceCertificate` elementu są identyczne z atrybutami [ \<ClientCertificate >](clientcertificate-of-clientcredentials-element.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
