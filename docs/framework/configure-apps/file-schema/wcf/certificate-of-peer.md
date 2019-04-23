---
title: <certificate> dla <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 5fdcb94e0c252d0bf5c215c08d44061bfe09a537
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120708"
---
# <a name="certificate-of-peer"></a>\<certyfikat > z \<elementu równorzędnego >
Określa certyfikat używany przez element równorzędny.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<peer>  
\<certificate>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509. Typ zawartych w atrybucie musi spełniać wymagania określonego `x509FindType`. Wartość domyślna to ciąg pusty.|  
|`storeLocation`|Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu węzła równorzędnego. Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine.|  
|`storeName`|Określa nazwę magazynu certyfikatu X.509 do otwarcia. Prawidłowe wartości są następujące:<br /><br /> — Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />-Urząd certyfikacji: Magazyn certyfikatów dla certyfikatów pośrednich urzędów certyfikacji.<br />-Niedozwolone: Magazyn certyfikatów dla odwołanych certyfikatów.<br />-Mój: Magazyn certyfikatów dla certyfikatów osobistych.<br />-Katalog główny: Magazyn certyfikatów zaufanych głównych urzędów certyfikacji (CA).<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Mój.|  
|`X509FindType`|Określa typ wyszukania X.509 w celu wykonania. Prawidłowe wartości są następujące:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Typ zawarty w `findValue` atrybut musi spełniać wymagania określonego `X509FindType`.<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<elementu równorzędnego >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Określa bieżące poświadczenia dla węzła równorzędnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji zawiera `X509Certificate2` wystąpienie używane podczas uwierzytelniania sąsiadów w siatki elementów równorzędnych.  
  
 Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Sieci równorzędne](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Uwierzytelnianie wiadomości z kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
