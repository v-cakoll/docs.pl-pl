---
title: <certificateReference> Aby uzyskać <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 93a6290d780ff61756f7315cd0c32f0e199ca00f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849985"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > dla \<tożsamości >
Określa ustawienia dla walidacji certyfikatu X. 509. Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością, sprawdza, czy oświadczenia przedstawione przez serwer zawierają oświadczenie tożsamości użyte do skonstruowania tej tożsamości.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tożsamości**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**  
  
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
|findValue|Określa wartość do wyszukania w magazynie certyfikatów X. 509. Typ zawarty w tym atrybucie musi spełniać wymagania określonej `X509FindType` wartości. Wartość domyślna to pusty ciąg.|  
|isChainIncluded|Wartość logiczna określająca, czy Walidacja jest wykonana przy użyciu łańcucha certyfikatów.|  
|storeLocation|Określa lokalizację magazynu certyfikatów, którego może użyć klient do zweryfikowania certyfikatu serwera.<br /><br /> Prawidłowe wartości to:<br /><br /> LocalMachine Magazyn certyfikatów przypisany do komputera lokalnego.<br />CurrentUser Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartość domyślna to LocalMachine.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Określa nazwę magazynu certyfikatu X. 509 do otwarcia.<br /><br /> Prawidłowe wartości to:<br /><br /> - AddressBook: Magazyn certyfikatów dla innych użytkowników.<br />AuthRoot Magazyn certyfikatów dla urzędów certyfikacji innych firm (CAs).<br />Urząd certyfikacji Magazyn certyfikatów dla pośrednich urzędów certyfikacji.<br />Niedozwolone Magazyn certyfikatów dla odwołanych certyfikatów.<br />Komputer Magazyn certyfikatów dla certyfikatów osobistych.<br />Pierwiastek Magazyn certyfikatów dla zaufanych głównych urzędów certyfikacji.<br />TrustedPeople Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />- TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to my.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Określa typ wyszukiwania X. 509, który ma zostać wykonany. Typ zawarty w `findValue` atrybucie musi spełniać wymagania określone X509FindType.<br /><br /> Prawidłowe wartości to:<br /><br /> - FindByThumbPrint<br />- FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />- FindBySerialNumber<br />- FindByTimeValid<br />- FindByTimeNotYetValid<br />- FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />- FindByKeyUsage<br />- FindBySubjectKeyIdentifier<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> tożsamości](identity.md)|Określa ustawienia, które umożliwiają uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
