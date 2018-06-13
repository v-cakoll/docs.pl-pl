---
title: '&lt;add&gt; w &lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 0192c14d5ebc0c84859878b35770e03843b2dd50
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752991"
---
# <a name="ltaddgt-of-ltknowncertificatesgt"></a>&lt;add&gt; w &lt;knownCertificates&gt;
Dodaje certyfikat X.509 do kolekcji znanych certyfikatów.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<issuedTokenAuthentication >  
\<knownCertificates >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<knownCertificates>   
   <add findValue="String"  
      storeLocation="CurrentUser/LocalMachine"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|findValue|Ciąg. Wartość do wyszukania.|  
|storeLocation|Wyliczenie. Jedna z dwóch lokalizacji przechowywania do wyszukiwania.|  
|storeName|Wyliczenie. Jednym z systemów magazynowania do wyszukiwania.|  
|X509FindType|Wyliczenie. Jedno z pól certyfikatu do wyszukiwania.|  
  
## <a name="findvalue-attribute"></a>findValue atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Wartość jest zależna od pola (określony przez atrybut X509FindType) przeszukiwany. Na przykład wyszukiwania odcisk palca, wartość musi być ciągiem szesnastkowym liczb.|  
  
## <a name="x509findtype-attribute"></a>Atrybut x509FindType  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości to: postać FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Lub LocalMachine CurrentUser.|  
  
## <a name="storename-attribute"></a>storeName atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości to: książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, głównego, TrustedPeople i TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|Reprezentuje kolekcję certyfikatów X.509, które są udostępniane przez zabezpieczenia tokenu usługi (STS) do sprawdzania poprawności tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Wystawiony token scenariusz ma trzy etapy. Podczas pierwszego etapu klienta próby uzyskania dostępu do usługi jest określane *secure token service*. Bezpieczne usługi tokenu następnie uwierzytelnia klientów i następnie wystawia token, zwykle tokenu zabezpieczeń potwierdzenia Markup Language (SAML) klienta. Klient następnie wróci do usługi z tokenem. Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelnienia tokenu, a w związku z tym klientem. W celu uwierzytelnienia tokenu certyfikat używa bezpiecznego tokenu usługi musi być znane z usługą.  
  
 [ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów bezpiecznego tokenu usługi. Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<Dodaj > element \<knownCertificates > elementu](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Domyślnie certyfikaty musi pochodzić od bezpiecznego usługi tokenu. Te "znane" certyfikatów, upewnij się, że tylko prawnie klientów dostępu do usługi.  
  
 Aby przejrzeć warunki wymagane do klienta może zostać uwierzytelniony przez usługi federacyjnej, jak również więcej informacji na temat używania tego elementu konfiguracji, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia dodanie certyfikatu do repozytorium dla wszystkich certyfikatów usługi STS.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <serviceCredentials>  
   <issuedTokenAuthentication>  
    <knownCertificates>  
     <add findValue="www.contoso.com" storeLocation="LocalMachine"   
           storeName="CertificateAuthority"  
           x509FindType="FindByIssuerName" />  
     </knownCertificates>  
    </issuedTokenAuthentication>  
   </serviceCredentials>  
  </behavior>  
 </serviceBehaviors>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
