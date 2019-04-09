---
title: <defaultCertificate> Element
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: c94531d10b7c0ef5ca0ee1f2d5683d0a259a2537
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100603"
---
# <a name="defaultcertificate-element"></a>\<defaultCertificate> Element
Określa certyfikat X.509, który ma być używany gdy usługa lub STS nie zapewnia go poprzez protokół negocjacji.  
  
 \<system.ServiceModel>  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials>  
\<serviceCertificate>  
\<defaultCertificate>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|findValue|ciąg. Wartość do wyszukania.|  
|x509FindType|Wyliczenie. Jedno z pól certyfikatu do wyszukiwania.|  
|storeLocation|Wyliczenie. Jedną z dwóch systemów przechowywania lokalizacji do przeszukania.|  
|storeName|Wyliczenie. Jednym z systemów magazynowania do wyszukiwania.|  
  
## <a name="findvalue-attribute"></a>findValue atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Wartość zależy od pola (określony przez atrybut X509FindType) wyszukiwany. Na przykład jeśli wyszukiwanie odcisku palca, wartość musi być ciągiem liczb szesnastkowych.|  
  
## <a name="x509findtype-attribute"></a>x509FindType Attribute  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|CurrentUser lub LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości: Książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, główny, TrustedPeople i TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Określa certyfikat używany podczas uwierzytelniania usługi dla klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Dla powiązań, które korzystają z zabezpieczeń komunikatów opartego na certyfikatach certyfikatu określonego przez ten element konfiguracji jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta. Przechowuje jeden certyfikat, który ma być używany, gdy żaden certyfikat nie jest określona przez usługę.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono certyfikat do użycia dla punktów końcowych, którego identyfikator URI rozpoczyna się od `http://www.contoso.com` i certyfikat do użycia dla wszystkich innych punktów końcowych, które nie wykonują negocjacji certyfikatu.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [\<authentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [Zabezpieczanie klientów [WCF]](../../../../../docs/framework/wcf/securing-clients.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
