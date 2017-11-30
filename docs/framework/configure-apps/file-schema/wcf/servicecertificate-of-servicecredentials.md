---
title: '&lt;serviceCertificate&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee21218ad9dd9103b90cd7be00a172ad321ba266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCertificate&gt; w &lt;serviceCredentials&gt;
Określ certyfikat X.509 używany do uwierzytelniania usługi dla klientów używających trybu zabezpieczenia wiadomości.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<serviceCertificate >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509. Typ zawartych w atrybucie muszą spełniać wymagania X509FindType określony. Wartość domyślna to ciąg pusty.|  
|`storeLocation`|Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu serwera. Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna jest komputer lokalny.|  
|`storeName`|Określa nazwę magazynu certyfikatu X.509 do otwarcia. Prawidłowe wartości są następujące:<br /><br /> -Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Certyfikatu sklepu dla firm urzędy certyfikacji (CA).<br />-CertificatAuthority: Magazyn certyfikatów dla pośrednie urzędy certyfikacji (CA).<br />— Niedozwolone: Magazyn certyfikatów odwołanych certyfikatów.<br />-Moje: Magazynu certyfikatów osobistych.<br />-Katalog główny: Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Moje.|  
|`x509FindType`|Określa typ wyszukiwania X.509 w celu wykonania. Prawidłowe wartości są następujące:<br /><br /> -Postać FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Typ zawarty w `findValue` atrybutu muszą spełniać wymagania X509FindType określony.<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia, które ma być używany podczas uwierzytelniania usługi, i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu, aby określić certyfikat X.509 używany do uwierzytelniania usługi dla klientów używających trybu zabezpieczenia wiadomości. Jeśli używasz certyfikatu, który będzie okresowo odnawiać jego odcisk palca zostanie zmieniona. W takim przypadku użyj nazwy podmiotu jako `x509FindType` ponieważ certyfikat może zostać wydany ponownie z taką samą nazwę podmiotu.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]za pomocą elementu, zobacz [porady: Określanie wartości poświadczeń klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [Porady: Określanie wartości poświadczeń klienta](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
