---
title: <scopedCertificates>, element
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: de85b3230461e876ec48e98887805d767e981e0f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270406"
---
# <a name="scopedcertificates-element"></a>\<scopedCertificates> Element
Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania. Ta kolekcja jest zazwyczaj pozwala ustalić certyfikaty usługi usługi tokenu zabezpieczeń w federacyjnym scenariuszu.  
  
 \<system.ServiceModel>  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials>  
\<serviceCertificate>  
\<scopedCertificates> Element  
\<Dodaj >, element dla \<scopedCertificates >  
  
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|Dodaje certyfikat X.509 do kolekcji certyfikatów będących w zakresie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Określa certyfikat używany podczas uwierzytelniania usługi dla klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Ta kolekcja umożliwia klienta skonfigurować certyfikaty usługi do użycia na podstawie adresu URL usługi, którym się komunikuje. Jest to szczególnie przydatne w wystawionych tokenów scenariuszach, gdzie klienta może się komunikować z wielu usług (service zakończenia także usługach tokenów zabezpieczeń pośrednie). Dla powiązań, które korzystają z zabezpieczeń komunikatów opartego na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi, a powinien być używany przez usługę do podpisywania odpowiedzi do klienta.  
  
 Jeśli powiązanie wymaga certyfikatu dla usługi i nie określonego certyfikatu dla usługi, którą można odnaleźć adresu URL w ScopedCertificates, jest używany certyfikat domyślny.  
  
 Aby uzyskać więcej informacji, zobacz sekcję "O zakresie certyfikatów" [jak: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono certyfikatu usługi dla klientów do użycia podczas komunikowania się z punktami końcowymi, których nazwa domeny jest `http://www.contoso.com` za pośrednictwem protokołu HTTP.  
  
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
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
