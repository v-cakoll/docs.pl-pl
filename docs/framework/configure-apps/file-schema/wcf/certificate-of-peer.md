---
title: '&lt;certificate&gt; w &lt;peer&gt;'
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 59aaee5549aae5df173174651ee3a520a0ac10fb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423458"
---
# <a name="ltcertificategt-of-ltpeergt"></a>&lt;certificate&gt; w &lt;peer&gt;
Określa certyfikat używany przez element równorzędny.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<elementu równorzędnego >  
\<certyfikat >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`findValue`|Ciąg, który zawiera wartość do wyszukania w magazynie certyfikatów X.509. Typ zawartych w atrybucie musi spełniać wymagania określonego `x509FindType`. Wartość domyślna to ciąg pusty.|  
|`storeLocation`|Określa lokalizację magazynu certyfikatu X.509, którego klient używa do walidacji certyfikatu węzła równorzędnego. Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine.|  
|`storeName`|Określa nazwę magazynu certyfikatu X.509 do otwarcia. Prawidłowe wartości są następujące:<br /><br /> — Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Certyfikatu sklep dla firm urzędy certyfikacji (CA).<br />-Urząd certyfikacji: Magazyn certyfikatów dla certyfikatów pośrednich urzędów certyfikacji.<br />-Niedozwolone: Certyfikatu magazynu dla odwołanych certyfikatów.<br />-Mój: Magazyn certyfikatów dla certyfikatów osobistych.<br />-Katalog główny: Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji (CA).<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Mój.|  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Sieci równorzędne](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Uwierzytelnianie wiadomości z kanału równorzędnego](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
