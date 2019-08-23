---
title: <defaultCertificate>, element
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919264"
---
# <a name="defaultcertificate-element"></a>\<defaultCertificate, element >
Określa certyfikat X. 509, który ma być używany, gdy usługa lub STS nie zapewnia go za pośrednictwem protokołu negocjacji.  
  
 \<system.ServiceModel>  
\<> zachowań  
Sekcja endpointBehaviors  
\<> zachowania  
\<clientCredentials>  
\<> serviceCertificate  
\<defaultCertificate>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|findValue|Parametry. Wartość do wyszukania.|  
|x509FindType|Licznik. Jedno z pól certyfikatów do przeszukania.|  
|storeLocation|Licznik. Jedna z dwóch lokalizacji magazynu systemowego do przeszukania.|  
|storeName|Licznik. Jeden z magazynów systemu do przeszukania.|  
  
## <a name="findvalue-attribute"></a>findValue — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Wartość jest zależna od pola (określonego przez atrybut X509FindType), który jest przeszukiwany. Na przykład, jeśli szukasz odcisku palca, wartość musi być ciągiem liczb szesnastkowych.|  
  
## <a name="x509findtype-attribute"></a>x509FindType — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Dostępne są następujące wartości: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|CurrentUser lub LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Dostępne są następujące wartości: AddressBook, AuthRoot, urząd certyfikacji, niedozwolone, my, root, TrustedPeople i TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> serviceCertificate](servicecertificate-of-clientcredentials-element.md)|Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach certyfikat określony przez ten element konfiguracji jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta. Przechowuje on pojedynczy certyfikat, który będzie używany w przypadku braku certyfikatu określonego przez usługę.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono certyfikat używany dla punktów końcowych, których identyfikator URI `http://www.contoso.com` zaczyna się od i certyfikat używany dla wszystkich innych punktów końcowych, które nie wykonują negocjacji certyfikatów.  
  
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
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [\<> uwierzytelniania](authentication-of-clientcertificate-element.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
