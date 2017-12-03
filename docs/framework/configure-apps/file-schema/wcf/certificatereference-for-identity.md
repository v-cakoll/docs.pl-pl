---
title: '&lt;certificateReference&gt; w &lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27bcccab90c4627f2c9a1d241af3b1833ae13a18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a>&lt;certificateReference&gt; w &lt;identity&gt;
Określa ustawienia dla walidacji certyfikatu X.509. Bezpieczny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klient łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają oświadczeń tożsamości użyta do skonstruowania tej tożsamości.  
  
 \<tożsamość >  
\<certificateReference >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|findValue|Określa wartość do wyszukania w magazynie certyfikatów X.509. Typ zawarte w tym atrybucie muszą spełniać wymagania określonego `X509FindType` wartość. Wartość domyślna to ciąg pusty.|  
|isChainIncluded|Wartość logiczna określająca, czy Walidacja jest wykonana przy użyciu łańcucha certyfikatów.|  
|storeLocation|Określa lokalizację magazynu certyfikatów, który klient może używać do weryfikacji certyfikatu serwera.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -LocalMachine: Magazyn certyfikatów przypisany na komputerze lokalnym.<br />-CurrentUser: Magazyn certyfikatów przypisany do bieżącego użytkownika.<br /><br /> Wartością domyślną jest komputer lokalny.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Określa nazwę magazynu certyfikatu X.509 do otwarcia.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -Książka adresowa: Magazyn certyfikatów dla innych użytkowników.<br />-AuthRoot: Certyfikatu sklepu dla firm urzędy certyfikacji (CA).<br />-Urzędów certyfikacji: Magazyn certyfikatów dla pośrednich urzędów certyfikacji.<br />— Niedozwolone: Magazyn certyfikatów odwołanych certyfikatów.<br />-Moje: Magazynu certyfikatów osobistych.<br />-Główny: Magazyn certyfikatów zaufanych głównych urzędów certyfikacji.<br />-TrustedPeople: Magazyn certyfikatów dla bezpośrednio zaufanych osób i zasobów.<br />-TrustedPublisher: Magazyn certyfikatów dla bezpośrednio zaufanych wydawców.<br /><br /> Wartość domyślna to Moje.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Określa typ wyszukiwania X.509 w celu wykonania. Typ zawarty w `findValue` atrybutu muszą spełniać wymagania X509FindType określony.<br /><br /> Prawidłowe wartości są następujące:<br /><br /> -Postać FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Wartość domyślna to FindBySubjectDistinguishedName.<br /><br /> Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa ustawienia, które umożliwiają uwierzytelnianie punkt końcowy przez inne punkty końcowe, wymiana wiadomości z nim.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>
