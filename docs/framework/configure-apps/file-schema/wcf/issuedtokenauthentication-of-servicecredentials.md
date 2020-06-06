---
title: <issuedTokenAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400358"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<issuedTokenAuthentication> dla \<serviceCredentials>
Określa niestandardowy token wystawiony jako poświadczenia usługi.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowedAudienceUris`|Pobiera zestaw docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienie. Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> .|  
|`allowUntrustedRsaIssuers`|Wartość logiczna określająca, czy są dozwolone niezaufane wystawcy certyfikatu RSA.<br /><br /> Certyfikaty są podpisywane przez urzędy certyfikacji w celu zweryfikowania autentyczności. Niezaufany wystawca to urząd certyfikacji, który nie został określony jako zaufany do podpisywania certyfikatów.|  
|`audienceUriMode`|Pobiera wartość określającą, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpieczający <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> ma być zweryfikowany. Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>. Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> .|  
|`certificateValidationMode`|Ustawia tryb walidacji certyfikatu. Jedna z prawidłowych wartości <xref:System.ServiceModel.Security.X509CertificateValidationMode> . Jeśli jest ustawiona na `Custom` , `customCertificateValidator` należy również podać wartość. Wartość domyślna to `ChainTrust`.|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` .|  
|`revocationMode`|Ustawia tryb odwołania, który określa, czy sprawdzanie odwołania odbywa się, a jeśli jest wykonywane w trybie online lub offline. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .|  
|`samlSerializer`|Opcjonalny atrybut ciągu, który określa typ elementu element SamlSerializer, który jest używany na potrzeby poświadczenia usługi. Wartość domyślna to pusty ciąg.|  
|`trustedStoreLocation`|Opcjonalne Wyliczenie. Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`knownCertificates`|Określa kolekcję <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementów, które określają zaufanych wystawców poświadczeń usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Scenariusz wystawionego tokenu ma trzy etapy. Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu*. Usługa Secure Tokens następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML). Klient następnie wraca do usługi przy użyciu tokenu. Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta. Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze.  
  
 Ten element jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. Aby dodać certyfikaty, użyj [\<knownCertificates>](knowncertificates.md) . Wstaw [\<add>](add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
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
  
 Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu. Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.  
  
 Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [How to: Configure Credentials in a a usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
