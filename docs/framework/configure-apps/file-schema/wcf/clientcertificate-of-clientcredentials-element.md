---
title: <clientCertificate> z <clientCredentials> — Element
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: 5abf0a99beff1b9fb3655cb82d74484f3b88237f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216460"
---
# <a name="clientcertificate-of-clientcredentials-element"></a>\<clientCertificate> of \<clientCredentials> Element
Definiuje certyfikat X.509 używany do uwierzytelniania klienta do usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<clientCredentials>  
\<clientCertificate>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509. Typ zawartych w atrybucie musi spełniać wymagania `X509FindType` wartość atrybutu. Wartość domyślna to ciąg pusty.|  
|`storeLocation`|Określa lokalizację certyfikatu X.509, używanego przez klienta do samodzielnego uwierzytelnienia usługi. Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|`storeName`|Określa nazwę magazynu certyfikatu X.509 do wyszukiwania. Prawidłowe wartości są następujące:<br /><br /> — Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />-Urząd certyfikacji: Magazyn certyfikatów dla certyfikatów pośrednich urzędów certyfikacji.<br />-Niedozwolone: Magazyn certyfikatów dla odwołanych certyfikatów.<br />-Mój: Magazyn certyfikatów dla certyfikatów osobistych.<br />-Katalog główny: Magazyn certyfikatów zaufanych głównych urzędów certyfikacji (CA).<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Mój. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Określa typ wyszukania X.509 w celu wykonania. Typ zawarty w `findValue` atrybut musi spełniać wymagania tego atrybutu. Prawidłowe wartości są następujące:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji określa certyfikat używany do uwierzytelniania klienta z tym elementem. Aby uzyskać więcej informacji, zobacz [jak: Określanie wartości poświadczeń klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Instrukcje: Określanie wartości poświadczeń klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [Zabezpieczanie klientów [WCF]](../../../../../docs/framework/wcf/securing-clients.md)
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
