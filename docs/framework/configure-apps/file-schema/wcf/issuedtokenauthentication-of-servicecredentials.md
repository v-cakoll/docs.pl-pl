---
title: '&lt;issuedTokenAuthentication&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1007abbb91787ed7be4fe3a7f8c1b0173191d60e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a>&lt;issuedTokenAuthentication&gt; w &lt;serviceCredentials&gt;
Określa niestandardowy token wydany jako poświadczenie usługi.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowedAudienceUris`|Pobiera zestaw docelowych identyfikatorów URI dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważany za prawidłowy przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia. Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Wartość logiczna określająca, czy są dozwolone niezaufani wystawcy certyfikatu.<br /><br /> Certyfikaty są podpisywane przez urzędy certyfikacji (CA) w celu sprawdzenia autentyczności. Wystawca niezaufanych jest urząd certyfikacji, który nie jest określony jako zaufane do podpisywania certyfikatów.|  
|`audienceUriMode`|Pobiera wartość, która określa, czy <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczającego <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> powinny być weryfikowane. Ta wartość jest typu <xref:System.IdentityModel.Selectors.AudienceUriMode>. Aby uzyskać więcej informacji na temat używania tego atrybutu, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Ustawia tryb walidacji certyfikatu. Jeden z prawidłowymi wartościami <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także. Wartość domyślna to `ChainTrust`.|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.|  
|`revocationMode`|Ustawia tryb odwołania, który określa, czy sprawdzanie odwołań występuje i czy jest wykonywane w trybie online lub offline. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Atrybut opcjonalny ciąg określający typ element SamlSerializer używanego dla poświadczenia usługi. Wartość domyślna to ciąg pusty.|  
|`trustedStoreLocation`|Opcjonalne wyliczenie. Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`knownCertificates`|Określa kolekcję <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementy, które określają zaufanymi wystawcami na potrzeby poświadczenie usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Wystawiony token scenariusz ma trzy etapy. Podczas pierwszego etapu klienta próby uzyskania dostępu do usługi jest określane *secure token service*. Bezpieczne usługi tokenu następnie uwierzytelnia klientów i następnie wystawia token, zwykle tokenu zabezpieczeń potwierdzenia Markup Language (SAML) klienta. Klient następnie wróci do usługi z tokenem. Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelnienia tokenu, a w związku z tym klientem. W celu uwierzytelnienia tokenu certyfikat używa bezpiecznego tokenu usługi musi być znane z usługą.  
  
 Ten element jest repozytorium dla wszystkich certyfikatów bezpiecznego tokenu usługi. Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Domyślnie certyfikaty musi pochodzić od bezpiecznego usługi tokenu. Te "znane" certyfikatów, upewnij się, że tylko prawnie klientów dostępu do usługi.  
  
 Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
