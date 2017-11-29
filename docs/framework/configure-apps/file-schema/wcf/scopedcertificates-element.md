---
title: '&lt;scopedCertificates&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ebcc5f640a585022c924994409dacbb06a08e47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltscopedcertificatesgt-element"></a>&lt;scopedCertificates&gt;, element
Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania. Ta kolekcja jest zwykle można określić certyfikaty usługi dla usługi tokenu zabezpieczeń w federacyjnym scenariuszu.  
  
 \<System. ServiceModel >  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials >  
\<serviceCertificate >  
\<scopedCertificates > — Element  
\<Dodaj > elementu \<scopedCertificates >  
  
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
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|Dodaje certyfikat X.509 do kolekcji certyfikatów będących w zakresie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|Określa certyfikat używany podczas uwierzytelniania usługi do klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Ta kolekcja umożliwia klientowi skonfigurować certyfikaty usługi do użycia na podstawie adresu URL usługi, z którym się komunikuje. Jest to szczególnie przydatne w wystawionego tokenu scenariuszach, gdzie klient może komunikować się wiele usług (usług a także usługi tokenu zabezpieczeń pośredniczące). Dla powiązań, które korzystają z zabezpieczeń wiadomości opartego na certyfikatach ten certyfikat jest używany do szyfrowania wiadomości do usługi, a powinien być używany przez usługę do podpisywania odpowiedzi do klienta.  
  
 Jeśli powiązanie wymaga certyfikatu dla usługi i nie określonego certyfikatu dla usługi, którą można odnaleźć adresu URL w ScopedCertificates, jest używany certyfikat domyślny.  
  
 Aby uzyskać więcej informacji, zobacz sekcję "O zakresie certyfikatów" [porady: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie certyfikat usługi dla klienta do użycia przy komunikacji z punktami końcowymi, których nazwa domeny jest http://www.contoso.com za pośrednictwem protokołu HTTP.  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Porady: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
