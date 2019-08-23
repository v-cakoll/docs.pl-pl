---
title: <serviceCertificate> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 36a228da262095bfe05d66c6d44ac73ba0ca401b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936314"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<> \<serviceCertificate >
Określ certyfikat X. 509, który zostanie użyty do uwierzytelnienia usługi dla klientów korzystających z trybu zabezpieczeń wiadomości.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<serviceCredentials>  
\<> serviceCertificate  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X. 509. Typ zawarty w atrybucie musi spełniać wymagania określone X509FindType. Wartość domyślna to pusty ciąg.|  
|`storeLocation`|Określa lokalizację magazynu certyfikatu X. 509, którego klient używa do weryfikacji certyfikatu serwera. Prawidłowe wartości to:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine.|  
|`storeName`|Określa nazwę magazynu certyfikatu X. 509 do otwarcia. Prawidłowe wartości to:<br /><br /> - AddressBook: Magazyn certyfikatów dla innych użytkowników.<br />AuthRoot Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />- CertificatAuthority: Magazyn certyfikatów dla pośrednich urzędów certyfikacji (CA).<br />Niedozwolone Magazyn certyfikatów dla odwołanych certyfikatów.<br />Komputer Magazyn certyfikatów dla certyfikatów osobistych.<br />Pierwiastek Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).<br />TrustedPeople Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />- TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to my.|  
|`x509FindType`|Określa typ wyszukiwania X. 509, który ma zostać wykonany. Prawidłowe wartości to:<br /><br /> - FindByThumbprint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Typ zawarty w `findValue` atrybucie musi spełniać wymagania określone X509FindType.<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi oraz ustawienia powiązane z walidacją poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu, aby określić certyfikat X. 509, który zostanie użyty do uwierzytelnienia usługi dla klientów korzystających z trybu zabezpieczeń wiadomości. Jeśli używasz certyfikatu, który będzie okresowo odnawiany, jego odcisk palca zmieni się. W takim przypadku należy użyć nazwy podmiotu jako `x509FindType` ponieważ certyfikat można wydać ponownie z tą samą nazwą podmiotu.  
  
 Aby uzyskać więcej informacji na temat korzystania z elementu [, zobacz How to: Określ wartości](../../../wcf/how-to-specify-client-credential-values.md)poświadczeń klienta.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Instrukcje: Określ wartości poświadczeń klienta](../../../wcf/how-to-specify-client-credential-values.md)
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
