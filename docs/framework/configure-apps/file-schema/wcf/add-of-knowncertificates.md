---
title: '&lt;add&gt; w &lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 1189b394669acb826342b0a250b39db738599495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579475"
---
# <a name="ltaddgt-of-ltknowncertificatesgt"></a>&lt;add&gt; w &lt;knownCertificates&gt;
Dodaje certyfikat X.509 do kolekcji znanych certyfikatów.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<issuedTokenAuthentication>  
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
|findValue|ciąg. Wartość do wyszukania.|  
|storeLocation|Wyliczenie. Jednym z dwóch lokalizacji przechowywania do wyszukiwania.|  
|storeName|Wyliczenie. Jednym z systemów magazynowania do wyszukiwania.|  
|x509FindType|Wyliczenie. Jedno z pól certyfikatu do wyszukiwania.|  
  
## <a name="findvalue-attribute"></a>findValue atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Wartość zależy od pola (określony przez atrybut X509FindType) wyszukiwany. Na przykład jeśli wyszukiwanie odcisku palca, wartość musi być ciągiem liczb szesnastkowych.|  
  
## <a name="x509findtype-attribute"></a>x509FindType Attribute  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|CurrentUser lub LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Wartości: Książka adresowa, AuthRoot, urząd certyfikacji, niedozwolone mojej, główny, TrustedPeople i TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|Reprezentuje kolekcję certyfikatów X.509, które są dostarczane przez Usługa tokenu zabezpieczającego (STS) do weryfikacji tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Wystawiony token scenariusz ma trzy etapy. W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service*. Usługa bezpiecznych tokenów następnie uwierzytelnia klienta, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta. Klient powraca do usługi przy użyciu tokenu. Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem. W celu uwierzytelnienia tokenu certyfikatu używa usługa bezpiecznych tokenów musi być znane, do usługi.  
  
 [ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów. Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<Dodaj > element \<knownCertificates > Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 Domyślnie certyfikaty musi pochodzić od usługa bezpiecznych tokenów. Te certyfikaty, upewnij się, że wiarygodnych tylko klienci "znane" Uzyskiwanie dostępu do usługi.  
  
 Aby przejrzeć warunki wymagane do klienta, może zostać uwierzytelniony przez usługi federacyjnej, jak również więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje certyfikat do repozytorium dla wszystkich certyfikatów usługi STS.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
