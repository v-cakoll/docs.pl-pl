---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152817"
---
# <a name="certificatereference"></a>\<> odniesienia certyfikatu
Określa ustawienia używane do znajdowania i sprawdzania poprawności certyfikatu X.509 w magazynie certyfikatów.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serwisCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>odniesienia certyfikatu**  
  
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
|Storename|Nazwa magazynu certyfikatów X.509. Wartość domyślna to "Moje". Element opcjonalny.|  
|Storelocation|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> określająca lokalizację magazynu certyfikatów X.509. Wartością domyślną jest "LocalMachine". Element opcjonalny.|  
|X509findtype|Wartość <xref:System.Security.Cryptography.X509Certificates.X509FindType> określająca typ wyszukiwania, które ma zostać wykonane. Wartość domyślna to "FindBySubjectDistinguishedName". Element opcjonalny.|  
|Findvalue|Wartość do wyszukania w magazynie certyfikatów X.509. Element opcjonalny.|  
|w zestawie isChain|Określa, czy sprawdzanie poprawności ma być wykonywane przy użyciu łańcucha certyfikatów. Wartość domyślna to "true"; sprawdzania poprawności odbywa się przy użyciu łańcucha certyfikatów. Element opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serwisCertificate>](servicecertificate.md)|Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<certificateReference>` określa ustawienia, które są używane do znajdowania i sprawdzania poprawności certyfikatu X.509 w magazynie certyfikatów. Gdy jest określony jako element `<serviceCertificate>` podrzędny elementu, określa ustawienia lokalizacji i weryfikacji certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów. Element `<certificateReference>` jest reprezentowany <xref:System.ServiceModel.Configuration.CertificateReferenceElement> przez klasę.
