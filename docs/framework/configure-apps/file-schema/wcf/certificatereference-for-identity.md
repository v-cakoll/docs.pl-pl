---
title: <certificateReference> dla <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 3b7779ac00c2fca6300c12ac18ff2d5f6b868424
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138817"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > dla \<identity >
Określa ustawienia dla walidacji certyfikatu X.509. Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia tożsamość użyta do skonstruowania tej tożsamości.  
  
 \<identity>  
\<certificateReference>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|findValue|Określa wartość do wyszukania w magazynie certyfikatów X.509. Typ zawarte w tym atrybucie musi spełniać wymagania określonego `X509FindType` wartość. Wartość domyślna to ciąg pusty.|  
|isChainIncluded|Wartość logiczna określająca, jeśli sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów.|  
|storeLocation|Określa lokalizację magazynu certyfikatów, który klient może używać na potrzeby weryfikacji certyfikatu serwera.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów, przypisany do komputera lokalnego.<br />-CurrentUser: Magazyn certyfikatów, przypisany do bieżącego użytkownika.<br /><br /> Wartością domyślną jest komputer lokalny.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Określa nazwę magazynu certyfikatu X.509 do otwarcia.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> — Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />-Urząd certyfikacji: Magazyn certyfikatów dla pośrednich urzędów certyfikacji.<br />-Niedozwolone: Magazyn certyfikatów dla odwołanych certyfikatów.<br />-Mój: Magazyn certyfikatów dla certyfikatów osobistych.<br />-Katalog główny: Magazyn certyfikatów zaufanych głównych urzędów certyfikacji.<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Mój.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Określa typ wyszukania X.509 w celu wykonania. Typ zawarty w `findValue` atrybut musi spełniać wymagania określonego X509FindType.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa ustawienia, które umożliwiają uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
