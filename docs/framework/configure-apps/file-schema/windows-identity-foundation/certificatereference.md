---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252143"
---
# <a name="certificatereference"></a>\<certificateReference >
Określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceCertificate**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**  
  
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
|storeName|Nazwa magazynu certyfikatów X. 509. Wartość domyślna to "my". Opcjonalny.|  
|storeLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość, która określa lokalizację magazynu certyfikatów X. 509. Wartość domyślna to "LocalMachine". Opcjonalna.|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość określająca typ wyszukiwania, które ma zostać wykonane. Wartość domyślna to "FindBySubjectDistinguishedName". Opcjonalny.|  
|findValue|Wartość do wyszukania w magazynie certyfikatów X. 509. Opcjonalna.|  
|isChainIncluded|Określa, czy należy przeprowadzić walidację przy użyciu łańcucha certyfikatów. Wartość domyślna to "true"; Walidacja jest przeprowadzana przy użyciu łańcucha certyfikatów. Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> serviceCertificate](servicecertificate.md)|Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 `<certificateReference>` Element określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów. Gdy jest określony jako element `<serviceCertificate>` podrzędny elementu, określa lokalizację i ustawienia weryfikacji certyfikatu X. 509, który jest używany do szyfrowania i odszyfrowywania tokenów. Element jest reprezentowany <xref:System.ServiceModel.Configuration.CertificateReferenceElement> przez klasę. `<certificateReference>`
