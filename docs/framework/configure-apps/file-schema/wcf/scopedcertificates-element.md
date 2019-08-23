---
title: <scopedCertificates>, element
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: ed53a42575a8d57c365f7a329a1a9c1df075d6d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935219"
---
# <a name="scopedcertificates-element"></a>\<scopedCertificates> Element
Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania. Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.  
  
 \<system.ServiceModel>  
\<> zachowań  
Sekcja endpointBehaviors  
\<> zachowania  
\<clientCredentials>  
\<> serviceCertificate  
\<scopedCertificates> Element  
\<Dodaj element > dla \<scopedCertificates >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|Dodaje certyfikat X. 509 do kolekcji certyfikatów z zakresem.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> serviceCertificate](servicecertificate-of-servicecredentials.md)|Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Ta kolekcja umożliwia klientowi skonfigurowanie certyfikatów usługi do użycia na podstawie adresu URL usługi, z którą komunikuje się. Jest to szczególnie przydatne w scenariuszach wystawionych tokenów, w których klient może komunikować się z wieloma usługami (usługą końcową oraz usługami tokenów zabezpieczających). W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.  
  
 Jeśli powiązanie wymaga certyfikatu dla usługi i nie zostanie znaleziony konkretny certyfikat dla adresu URL usługi w ScopedCertificates, zostanie użyty certyfikat domyślny.  
  
 Aby uzyskać więcej informacji, zobacz sekcję ["certyfikaty w zakresie", w jaki sposób: Utwórz klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)federacyjnego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono certyfikat usługi używany przez klienta podczas komunikacji z punktami końcowymi, których nazwa domeny `http://www.contoso.com` znajduje się za pośrednictwem protokołu HTTP.  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
