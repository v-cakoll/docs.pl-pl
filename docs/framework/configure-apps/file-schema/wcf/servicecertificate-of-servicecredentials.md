---
title: '&lt;serviceCertificate&gt; w &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: 6718804005d21cfdb75c27e417cb106aa05d79ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556327"
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCertificate&gt; w &lt;serviceCredentials&gt;
Określ certyfikat X.509, który będzie używany do uwierzytelniania usługi dla klientów używających trybu zabezpieczenia wiadomości.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<serviceCertificate>  
  
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
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509. Typ zawartych w atrybucie musi spełniać wymagania określonego X509FindType. Wartość domyślna to ciąg pusty.|  
|`storeLocation`|Określa lokalizację magazynu certyfikatu X.509, używanego przez klienta na potrzeby weryfikacji certyfikatu serwera względem. Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine.|  
|`storeName`|Określa nazwę magazynu certyfikatu X.509 do otwarcia. Prawidłowe wartości są następujące:<br /><br /> — Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />-CertificatAuthority: Magazyn certyfikatów dla pośrednie urzędy certyfikacji (CA).<br />-Niedozwolone: Magazyn certyfikatów dla odwołanych certyfikatów.<br />-Mój: Magazyn certyfikatów dla certyfikatów osobistych.<br />-Katalog główny: Magazyn certyfikatów zaufanych głównych urzędów certyfikacji (CA).<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Mój.|  
|`x509FindType`|Określa typ wyszukania X.509 w celu wykonania. Prawidłowe wartości są następujące:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Typ zawarty w `findValue` atrybut musi spełniać wymagania określonego X509FindType.<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenie do użycia w uwierzytelnianiu usługi i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu, aby określić certyfikat X.509, który będzie używany do uwierzytelniania usługi dla klientów używających trybu zabezpieczenia wiadomości. Jeśli używasz certyfikatu, który będzie okresowo odnawiać jego odcisk palca zostanie zmieniona. W takim przypadku użyj nazwy tematu jako `x509FindType` ponieważ certyfikat może zostać wydany ponownie o takiej samej nazwie podmiotu.  
  
 Aby uzyskać więcej informacji na temat za pomocą elementu zobacz [jak: Określanie wartości poświadczeń klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [Instrukcje: Określanie wartości poświadczeń klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
