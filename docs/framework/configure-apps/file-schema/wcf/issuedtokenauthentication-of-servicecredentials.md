---
title: <issuedTokenAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: d093b45269b230b4ff074d07a66290ab09592f60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756718"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<issuedTokenAuthentication > z \<serviceCredentials >
Określa niestandardowy token wydany jako poświadczenie usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<issuedTokenAuthentication>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowedAudienceUris`|Pobiera zestaw docelowych URI dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia. Aby uzyskać więcej informacji na temat korzystania z tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Wartość logiczna określająca, jeśli są dozwolone niezaufani wystawcy certyfikatu.<br /><br /> Certyfikaty są podpisane przez urzędy certyfikacji (CA) w celu sprawdzenia autentyczności. Niezaufane wystawca jest urząd certyfikacji, który nie jest określony jako zaufane do podpisywania certyfikatów.|  
|`audienceUriMode`|Pobiera wartość określającą, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpieczający <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> powinny być weryfikowane. Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>. Aby uzyskać więcej informacji na temat korzystania z tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Ustawia tryb walidacji certyfikatu. Jedną z prawidłowych wartości z <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony. Wartość domyślna to `ChainTrust`.|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.|  
|`revocationMode`|Ustawia tryb odwołania, który określa, czy sprawdzanie odwołań występuje i czy jest wykonywane w trybie online lub offline. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Atrybut opcjonalny ciąg, który określa typ element SamlSerializer używanego dla poświadczenia usługi. Wartość domyślna to ciąg pusty.|  
|`trustedStoreLocation`|Opcjonalne wyliczenie. Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`knownCertificates`|Określa kolekcję elementów <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementy, które określa zaufanymi wystawcami na potrzeby poświadczeń usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Wystawiony token scenariusz ma trzy etapy. W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service*. Usługa bezpiecznych tokenów następnie uwierzytelnia klienta, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta. Klient powraca do usługi przy użyciu tokenu. Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem. W celu uwierzytelnienia tokenu certyfikatu używa usługa bezpiecznych tokenów musi być znane, do usługi.  
  
 Ten element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów. Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
