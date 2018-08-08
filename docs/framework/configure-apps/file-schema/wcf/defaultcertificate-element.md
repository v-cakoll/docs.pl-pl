---
title: '&lt;defaultCertificate&gt;, element'
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: a4af1c6ec452b24634fa50162fa71f069e2451f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751015"
---
# <a name="ltdefaultcertificategt-element"></a>&lt;defaultCertificate&gt;, element
Określa certyfikat X.509 do użycia podczas usługa lub STS nie zapewnia go poprzez protokół negocjacji.  
  
 \<system.ServiceModel>  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials>  
\<serviceCertificate >  
\<defaultCertificate >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|findValue|Ciąg. Wartość do wyszukania.|  
|X509FindType|Wyliczenie. Jedno z pól certyfikatu do wyszukiwania.|  
|storeLocation|Wyliczenie. Jeden z dwóch systemów przechowywania lokalizacji do wyszukiwania.|  
|storeName|Wyliczenie. Jednym z systemów magazynowania do wyszukiwania.|  
  
## <a name="findvalue-attribute"></a>findValue atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Wartość jest zależna od pola (określony przez atrybut X509FindType) przeszukiwany. Na przykład wyszukiwania odcisk palca, wartość musi być ciągiem szesnastkowym liczb.|  
  
## <a name="x509findtype-attribute"></a>Atrybut x509FindType  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości to: postać FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Lub LocalMachine CurrentUser.|  
  
## <a name="storename-attribute"></a>storeName atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości to: książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, głównego, TrustedPeople i TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Określa certyfikat używany podczas uwierzytelniania usługi do klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Dla powiązań, które korzystają z zabezpieczeń wiadomości opartego na certyfikatach certyfikatu określonego przez ten element konfiguracji jest używany do szyfrowania wiadomości do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta. Przechowuje jeden certyfikat do użycia, gdy żaden certyfikat nie jest określona przez usługę.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie certyfikat do użycia dla punktów końcowych, którego identyfikator URI, który rozpoczyna się od http://www.contoso.com i certyfikat do użycia dla wszystkich innych punktów końcowych, które nie wykonuj negocjowanie certyfikatu.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [\<Uwierzytelnianie >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
