---
title: <certificate><clientCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 1af56280397e7d8924656f2f7cda5af4e30e91e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926191"
---
# <a name="certificate-of-clientcertificate-element"></a>\<> certyfikatu > \<elementu ClientCertificate
Określa certyfikat X. 509 używany do podpisywania i szyfrowania wiadomości.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<serviceCredentials>  
\<clientCertificate>  
\<> certyfikatów  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X. 509. Typ zawarty w atrybucie musi spełniać wymagania określone X509FindType. Wartość domyślna to pusty ciąg.|  
|`storeLocation`|Określa lokalizację magazynu certyfikatu X. 509, którego klient używa do weryfikacji certyfikatu serwera. Prawidłowe wartości to:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine.|  
|`storeName`|Określa nazwę magazynu certyfikatu X. 509 do otwarcia. Prawidłowe wartości to:<br /><br /> - AddressBook: Magazyn certyfikatów dla innych użytkowników.<br />AuthRoot Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />Urząd certyfikacji Magazyn certyfikatów dla pośrednich urzędów certyfikacji (CA).<br />Niedozwolone Magazyn certyfikatów dla odwołanych certyfikatów.<br />Komputer Magazyn certyfikatów dla certyfikatów osobistych.<br />Pierwiastek Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).<br />TrustedPeople Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />- TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to my.|  
|`X509FindType`|Określa typ wyszukiwania X. 509, który ma zostać wykonany. Prawidłowe wartości to:<br /><br /> - FindByThumbPrint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Typ zawarty w `findValue` atrybucie musi spełniać wymagania określone X509FindType.<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> clientCertificate](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Uwagi  
 Ten `<certificate>` element jest używany, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem. Dzieje się tak w przypadku używania wzorca komunikacji dupleksowej. W przypadku bardziej typowego wzorca żądania/odpowiedzi klient zawiera swój certyfikat w żądaniu, którego usługa używa do szyfrowania i podpisywania odpowiedzi z powrotem do klienta. W przypadku wzorca komunikacji dupleksowej usługa nie ma jednak żądania od klienta i w związku z tym potrzebuje certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć komunikat do klienta. W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem i określić certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usług dupleksowych, zobacz [How to: Utwórz kontrakt](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)dupleksowy.  
  
## <a name="example"></a>Przykład  
 Poniższy kod określa, jak znaleźć odpowiedni certyfikat X. 509 i niestandardowy typ walidacji w `<authentication>` elemencie.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
