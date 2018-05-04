---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0f9a826a4c8d292346d9efee7970a82b88fb612
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificatereferencegt"></a>&lt;certificateReference&gt;
Określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<serviceCertificate >  
\<certificateReference >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|storeName|Nazwa magazynu certyfikatu X.509. Wartość domyślna to "Moje". Opcjonalna.|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa lokalizację magazynu certyfikatu X.509. Wartością domyślną jest "Komputer lokalny". Opcjonalna.|  
|X509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość, która określa typ wyszukiwania, która ma zostać wykonana. Wartość domyślna to "FindBySubjectDistinguishedName". Opcjonalna.|  
|findValue|Wartość do wyszukania w magazynie certyfikatów X.509. Opcjonalna.|  
|isChainIncluded|Określa, czy Weryfikacja ma zostać wykonane przy użyciu łańcucha certyfikatów. Wartość domyślna to "true"; Sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów. Opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|Określa certyfikat, który jest używany do szyfrowania i odszyfrowywania tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 `<certificateReference>` Element określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509. Jeśli jest określony jako element podrzędny elementu `<serviceCertficate>` elementu, określa ustawienia lokalizacji i weryfikacja certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów. `<certificateReference>` Reprezentowany przez element <xref:System.ServiceModel.Configuration.CertificateReferenceElement> klasy.
