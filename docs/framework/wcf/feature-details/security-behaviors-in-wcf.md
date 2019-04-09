---
title: Zachowania zabezpieczeń w programie WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: d1bffef127fe295aa41b1287da1c7104464ae0bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180066"
---
# <a name="security-behaviors-in-wcf"></a>Zachowania zabezpieczeń w programie WCF
W konsoli Windows Communication Foundation (WCF) zachowania zmodyfikować zachowanie w czasie wykonywania na poziomie usługi, lub na poziomie punktu końcowego. (Aby uzyskać więcej informacji na temat zachowań ogólnie rzecz biorąc, zobacz [Określanie zachowania środowiska uruchomieniowego usługi](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Zachowania zabezpieczeń* umożliwić kontrolę nad poświadczeniami, uwierzytelniania, autoryzacji i dzienniki inspekcji. Można użyć zachowań, programowania lub za pośrednictwem konfiguracji. Ten temat koncentruje się na temat konfigurowania następujące zachowania związane z funkcjami zabezpieczeń:  
  
-   [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata w pliku >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), które również pozwala na określenie bezpiecznego punktu końcowego, który klienci mogą uzyskiwać dostęp do metadanych.  
  
## <a name="setting-credentials-with-behaviors"></a>Ustawianie poświadczeń za pomocą zachowań  
 Użyj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) i [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) do ustawiania wartości poświadczeń klienta lub usługi. Bazowej konfiguracji powiązania Określa, czy poświadczenia musi zostać ustawione. Na przykład, jeśli tryb zabezpieczeń jest ustawiony na `None`, klientów i usług nie wzajemne uwierzytelnianie i wymagane żadne poświadczenia nie dowolnego typu.  
  
 Z drugiej strony powiązanie usługi może wymagać typu poświadczeń klienta. W takim przypadku trzeba ustawić wartość poświadczenia, za pomocą zachowania. (Aby uzyskać więcej informacji na temat możliwych typów poświadczeń, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) W niektórych przypadkach, np. gdy poświadczenia Windows są używane do uwierzytelniania środowisko automatycznie zestawia wartości rzeczywiste poświadczenia i nie trzeba jawnie ustawić wartość poświadczenia (Jeśli nie chcesz określić innego zestawu poświadczeń).  
  
 Wszystkie poświadczenia usługi są dostępne jako elementy podrzędne [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Poniższy przykład przedstawia certyfikat używany jako poświadczenie usługi.  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>Poświadczenia usługi  
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zawiera cztery elementy podrzędne. W poniższych sekcjach omówiono elementów i ich użycia.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Użyj tego elementu, aby określić certyfikat X.509, który jest używany do uwierzytelniania usługi dla klientów używających trybu zabezpieczenia wiadomości. Jeśli używasz certyfikatu, który jest okresowo odnawiać, następnie zmiany jego odcisk palca. W takim przypadku użyj nazwy tematu jako `X509FindType` ponieważ certyfikat może zostać wydany ponownie o takiej samej nazwie podmiotu.  
  
 Aby uzyskać więcej informacji na temat za pomocą elementu zobacz [jak: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certyfikat > z \<clientCertificate > Element  
 Użyj [ \<certyfikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) elementu w przypadku usługi musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem. Dzieje się tak, korzystając z paradygmacie komunikacji dupleksowej. W bardziej typowy wzorzec "żądanie-odpowiedź" klient dołącza swój certyfikat w żądaniu, w której usługa secure jego odpowiedź z powrotem do klienta. Paradygmacie komunikacji dupleksowej, jednak nie ma żądań i odpowiedzi. Usługa nie można wywnioskować certyfikat klienta z komunikacji i w związku z tym usługa wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomości do klienta. Należy uzyskać certyfikat klienta w sposób out-of-band i Określ certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<Uwierzytelnianie > z \<clientCertificate > Element  
 [ \<Uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) elementu pozwala na dostosowanie, sposób uwierzytelniania klientów. Możesz ustawić `CertificateValidationMode` atrybutu `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, lub `Custom`. Domyślnie ustawiono poziom `ChainTrust`, która określa, że każdy certyfikat musi zostać znaleziony w hierarchii certyfikatów kończy się rozszerzeniem *główny urząd* w górnej części łańcucha. Jest to najbezpieczniejsza opcja Tryb. Można również ustawić wartość, `PeerOrChainTrust`, która określa, że własnym wystawionych certyfikatów (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w zaufanym łańcuchem. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawionych certyfikatów nie należy zakupić od zaufanego urzędu. Podczas wdrażania klienta, użyj `ChainTrust` jest wartość. Można również ustawić wartość, `Custom`. Po ustawieniu `Custom` wartości, należy także ustawić `CustomCertificateValidatorType` atrybutu do zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, musi dziedziczyć abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> Element  
 Wystawiony token scenariusz ma trzy etapy. W pierwszym etapie klienta próby uzyskania dostępu do usługi jest określane *secure token service* (STS). Usługa STS następnie uwierzytelnia klientów, a następnie wystawia token, zazwyczaj token zabezpieczeń potwierdzenia Markup Language (SAML) klienta. Klient powraca do usługi przy użyciu tokenu. Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelniania tokenu, a w związku z tym klientem. W celu uwierzytelnienia tokenu certyfikatu, który używa usługa bezpiecznych tokenów musi być znane, do usługi. [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów usługa bezpiecznych tokenów. Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Domyślnie certyfikaty musi pochodzić od usługa bezpiecznych tokenów. Te certyfikaty, upewnij się, że wiarygodnych tylko klienci "znane" Uzyskiwanie dostępu do usługi.  
  
 Należy używać [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) kolekcji w aplikacji federacyjnych, która korzysta z *secure token service* (STS), który wystawia `SamlSecurityToken` tokenów zabezpieczających. Gdy Usługa STS wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie `SamlAudienceRestrictionCondition` do tokenu zabezpieczającego. Umożliwiająca `SamlSecurityTokenAuthenticator` odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test ma się zdarzyć, wykonując następujące czynności:  
  
-   Ustaw `audienceUriMode` atrybutu [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) do `Always` lub `BearerKeyOnly`.  
  
-   Określ zbiór prawidłowe identyfikatory URI, dodając identyfikatory URI do tej kolekcji. Aby to zrobić, należy wstawić [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) dla każdego identyfikatora URI  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji o używaniu ten element konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Zezwalanie użytkownikom anonimowym CardSpace  
 Ustawienie `AllowUntrustedRsaIssuers` atrybutu `<IssuedTokenAuthentication>` elementu `true` jawnie umożliwia dowolnego klienta przedstawić token wystawiony samodzielnie podpisany przy użyciu dowolnego pary kluczy RSA. Wystawca ma *niezaufanych* ponieważ klucz nie zawiera wystawcy danych skojarzonych z nim. A [!INCLUDE[infocard](../../../../includes/infocard-md.md)] użytkownik może utworzyć własny wystawionego kartę, która zawiera własny podana oświadczeń tożsamości. Tej funkcji należy używać ostrożnie. Aby użyć tej funkcji, pomyśl o klucz publiczny RSA jako bardziej bezpiecznym hasłem, które mają być przechowywane w bazie danych wraz z nazwą użytkownika. Przed zezwoleniem na dostęp klienta do usługi, sprawdź klient przedstawiony klucz publiczny RSA, porównując go z kluczem publicznym przechowywanych dla nazwy użytkownika przedstawiony. Przy założeniu, że ustanowiono procesu rejestracji, według których użytkownicy mogą zarejestrować swoje nazwy użytkownika i skojarz je z własnym wystawiony klucze publiczne RSA.  
  
## <a name="client-credentials"></a>Poświadczenia klienta  
 Poświadczenia klienta są używane do uwierzytelniania klienta do usługi w przypadkach, gdy jest wymagane uwierzytelnianie wzajemne. Aby określić certyfikaty usługi dla scenariuszy gdzie klienta należy zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi, można użyć sekcji.  
  
 Można także skonfigurować klienta jako część scenariusz Federacji do użycia wystawione tokeny usługa bezpiecznych tokenów lub lokalnego wystawcy tokenów. Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Wszystkie poświadczenia klienta znajdują się w obszarze [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak pokazano w poniższym kodzie.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### <a name="clientcertifictate-element"></a>\<clientCertifictate> Element  
 Ustaw certyfikat używany do uwierzytelniania klienta z tym elementem. Aby uzyskać więcej informacji, zobacz [jak: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Ta funkcja wymaga włączenia w usłudze Active Directory, Windows i Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken > Element  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) zawiera elementy umożliwia konfigurowanie lokalnego wystawcy tokenów lub zachowania używane z usługi tokenu zabezpieczającego. Aby uzyskać instrukcje na temat konfigurowania klienta Użyj wystawcy lokalnego, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 Określa domyślny adres usługi tokenu zabezpieczeń. Jest on używany podczas <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adres URL dla usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null`. W takich przypadkach <xref:System.ServiceModel.Description.ClientCredentials> musi być skonfigurowany za pomocą adresu lokalnego wystawcy i powiązanie, aby używać do komunikowania się z tym wystawcą.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 Użyj [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) dodać zachowań klienta WCF, używane podczas komunikacji z usługi tokenu zabezpieczającego. Definiowanie zachowania klienta w [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) sekcji. Aby użyć zdefiniowanego zachowania, należy dodać <`add`> elementu `<issuerChannelBehaviors>` elementu o dwa atrybuty. Ustaw `issuerAddress` do adresu URL usługi tokenów zabezpieczeń i ustaw `behaviorConfiguration` atrybutu Nazwa zachowania zdefiniowanego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Użyj tego elementu do kontrolowania uwierzytelniania certyfikatów usługi.  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) elementu można przechowywać jeden certyfikat używany, gdy usługa określa żadnego certyfikatu.  
  
 Użyj [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) i [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) można ustawić certyfikaty usługi, które są skojarzone z określonymi usługami. `<add>` Element zawiera `targetUri` atrybut, który jest używany do skojarzyć certyfikat z usługą.  
  
 [ \<Uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element określa poziom zaufania, używany do uwierzytelniania certyfikatów. Domyślnie ustawiono poziom "ChainTrust", który określa, że każdy certyfikat musi zostać znaleziony w hierarchii końcówce zaufanego urzędu certyfikacji w górnej części łańcucha certyfikatów. Jest to najbezpieczniejsza opcja Tryb. Można również ustawić wartość "PeerOrChainTrust", który określa, że własnym wystawionych certyfikatów (relacja zaufania elementów równorzędnych) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchem. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawionych certyfikatów nie należy zakupić od zaufanego urzędu. Podczas wdrażania klienta, należy użyć wartości "ChainTrust". Można również ustawić wartość "Niestandardowe" lub "None". Aby użyć wartości "Niestandardowy", należy także ustawić `CustomCertificateValidatorType` atrybutu do zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, musi dziedziczyć abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element zawiera `RevocationMode` atrybut określający, jak certyfikaty są sprawdzane pod kątem odwołań. Wartość domyślna to "online", co oznacza, że certyfikaty są automatycznie sprawdzane pod kątem odwołań. Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) element zawiera elementy, które wpływają na autoryzacji, ról niestandardowych dostawców i personifikacji.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Klasy jest stosowany do metody usługi. Ten atrybut określa grupy użytkowników do użycia podczas nadanie Metoda chroniona. Wartością domyślną jest "UseWindowsGroups" i określa, czy grupy Windows, takie jak "Administratorzy" lub "Użytkowników", są przeszukiwane pod kątem tożsamości próby uzyskania dostępu do zasobu. Można również określić "UseAspNetRoles" Używanie dostawcy roli niestandardowej, skonfigurowanego w obszarze <`system.web` > elementu, jak pokazano w poniższym kodzie.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Poniższy kod przedstawia `roleProviderName` używane z `principalPermissionMode` atrybutu.  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>Konfigurowanie inspekcji zabezpieczeń  
 Użyj [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) do określania dziennika zapisywane i jakie typy zdarzeń logowania. Aby uzyskać więcej informacji, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>Bezpiecznej wymiany metadanych  
 Eksportowanie metadanych dla klientów jest wygodne dla deweloperów usługi i klienta, jak umożliwia pobieranie kodu, konfiguracji i klienta. Aby zmniejszyć prawdopodobieństwo ujawnienia danych usługi do złośliwych użytkowników, istnieje możliwość bezpiecznego transferu za pomocą protokołu SSL za pośrednictwem mechanizmu HTTP (HTTPS). Aby to zrobić, możesz powiązać odpowiedniego certyfikatu X.509 do określonego portu, na komputerze, który jest hostem usługi. (Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Po drugie, Dodaj [ \<serviceMetadata w pliku >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do konfiguracji usługi i ustaw `HttpsGetEnabled` atrybutu `true`. Wreszcie, ustaw `HttpsGetUrl` atrybutu do adresu URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
