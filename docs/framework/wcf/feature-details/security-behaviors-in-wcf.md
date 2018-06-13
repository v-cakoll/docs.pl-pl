---
title: Zachowania zabezpieczeń w programie WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 57bd34c72e98091c4a429d683a0da4ce2d3967c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508647"
---
# <a name="security-behaviors-in-wcf"></a>Zachowania zabezpieczeń w programie WCF
W konsoli Windows Communication Foundation (WCF) zachowania modyfikowanie zachowania w czasie wykonywania na poziomie usługi lub na poziomie punktu końcowego. (Aby uzyskać więcej informacji na temat zachowania ogólnie rzecz biorąc, zobacz [Określanie zachowania środowiska uruchomieniowego usługi](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Zachowania zabezpieczeń* umożliwiają kontrolę nad poświadczeniami, uwierzytelniania, autoryzacji i dzienniki inspekcji. Można użyć zachowania, przez programowania w języku lub przy użyciu konfiguracji. Ten temat koncentruje się na konfigurowaniu następujące zachowania związane z funkcjami zabezpieczeń:  
  
-   [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), który umożliwia także określić punkt końcowy bezpieczny, którego klienci mogą uzyskiwać dostęp do metadanych.  
  
## <a name="setting-credentials-with-behaviors"></a>Ustawianie poświadczeń za pomocą zachowań  
 Użyj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) i [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) można ustawić wartości poświadczeń dla danej usługi lub klienta. Podstawowej konfiguracji powiązania Określa, czy poświadczenia musi zostać ustawione. Na przykład, jeśli tryb zabezpieczeń jest ustawiony na `None`, klientów i usług nie wzajemne uwierzytelnianie i wymagają żadnych poświadczeń dowolnego typu.  
  
 Z drugiej strony powiązanie usługi może wymagać typu poświadczeń klienta. W takim przypadku należy ustawić wartość poświadczeń za pomocą zachowania. (Aby uzyskać więcej informacji na temat możliwych typów poświadczeń, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) W niektórych przypadkach, takich jak kiedy poświadczeń systemu Windows są używane do uwierzytelniania środowisko automatycznie ustala wartość rzeczywista poświadczenia i nie trzeba jawnie ustawiona wartość poświadczenia (chyba że chcesz określić inny zestaw poświadczeń).  
  
 Wszystkie poświadczenia usługi są dostępne jako elementy podrzędne [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). W poniższym przykładzie przedstawiono certyfikat jest używany jako poświadczenie usługi.  
  
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
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zawiera cztery elementy podrzędne. W poniższych sekcjach opisano elementy i ich użycia.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > — Element  
 Użyj tego elementu, aby określić certyfikat X.509, który jest używany do uwierzytelniania usługi dla klientów używających trybu zabezpieczenia wiadomości. Jeśli używasz certyfikatu, który okresowo odnawiać, następnie zmiany jego odcisk palca. W takim przypadku użyj nazwy podmiotu jako `X509FindType` ponieważ certyfikat może zostać wydany ponownie z taką samą nazwę podmiotu.  
  
 Aby uzyskać więcej informacji o korzystaniu z elementu, zobacz [porady: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certyfikat > z \<clientCertificate > — Element  
 Użyj [ \<certyfikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) elementu, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem. Dzieje się tak podczas używania wzorca komunikację dupleksową. We wzorcu bardziej typowego żądanie odpowiedź klienta obejmuje jego certyfikat w żądaniu, w której usługa secure swojej odpowiedzi do klienta. Wzorzec komunikację dupleksową, jednak nie ma żądań i odpowiedzi. Nie można wnioskować o usługę certyfikatu klienta z komunikacji i w związku z tym usługa wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomości do klienta. Należy uzyskać certyfikat klienta w sposób poza pasmem i Określ certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<Uwierzytelnianie > z \<clientCertificate > — Element  
 [ \<Uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element umożliwia dostosowanie sposobu uwierzytelniania klientów. Można ustawić `CertificateValidationMode` atrybutu `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, lub `Custom`. Domyślnie po ustawieniu poziomu `ChainTrust`, który określa, że każdy certyfikat musi zostać znaleziony w hierarchii certyfikatów w *główny urząd* w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość `PeerOrChainTrust`, która określa, że certyfikaty wystawionej samodzielnie (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w łańcuchu zaufanego. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawione certyfikaty nie muszą można zakupić z zaufanego urzędu. Podczas wdrażania klienta, użyj `ChainTrust` wartość zmiennej. Można również ustawić wartość `Custom`. Jeśli wartość `Custom` wartości, należy także ustawić `CustomCertificateValidatorType` atrybutu zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własnego niestandardowego modułu weryfikacji, musi dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication > — Element  
 Wystawiony token scenariusz ma trzy etapy. Podczas pierwszego etapu klienta próby uzyskania dostępu do usługi jest określane *secure token service* (STS). Usługa tokenu Zabezpieczającego następnie uwierzytelnia klientów, a następnie wystawia token, zwykle tokenu zabezpieczeń potwierdzenia Markup Language (SAML) klienta. Klient następnie wróci do usługi z tokenem. Usługa sprawdza, czy token dla danych, które umożliwia usłudze uwierzytelnienia tokenu, a w związku z tym klientem. W celu uwierzytelnienia tokenu certyfikatu, który używa bezpiecznego tokenu usługi musi być znane z usługą. [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element jest repozytorium dla wszystkich certyfikatów bezpiecznego tokenu usługi. Aby dodać certyfikaty, należy użyć [ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
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
  
 Należy używać [ \<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) kolekcji w aplikacji federacyjnych, która korzysta z *secure token service* (STS), który wystawia `SamlSecurityToken` tokenów zabezpieczających. Jeśli usługa tokenu Zabezpieczającego wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie `SamlAudienceRestrictionCondition` do tokenu zabezpieczającego. Która umożliwia `SamlSecurityTokenAuthenticator` odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test powinno się zdarzyć, wykonując następujące czynności:  
  
-   Ustaw `audienceUriMode` atrybutu [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) do `Always` lub `BearerKeyOnly`.  
  
-   Określ zbiór prawidłowymi identyfikatorami URI, dodając identyfikatory URI do tej kolekcji. Aby to zrobić, Wstaw [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) dla każdego identyfikatora URI  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Zezwalanie użytkownikom anonimowym CardSpace  
 Ustawienie `AllowUntrustedRsaIssuers` atrybutu `<IssuedTokenAuthentication>` elementu `true` jawnie zezwala dowolnego klienta do prezentowania samodzielnie wystawionego tokenu, podpisany z dowolnego parę kluczy RSA. Wystawca ma *niezaufanych* ponieważ klucz nie zawiera wystawcy danych skojarzonych z nim. A [!INCLUDE[infocard](../../../../includes/infocard-md.md)] użytkownik może utworzyć karty wystawionej samodzielnie zawierającej własnym podana oświadczeń tożsamości. Użyj tej funkcji należy z rozwagą. Użyj tej funkcji, można wziąć pod uwagę klucza publicznego RSA jako bardziej bezpiecznym hasłem, które mają być przechowywane w bazie danych oraz nazwę użytkownika. Przed umożliwieniem dostępu klienta do usługi, sprawdź przedstawione przez klienta klucza publicznego RSA, porównując go z przechowywanych klucza publicznego dla nazwy użytkownika przedstawioną. To zakłada, że zostało ustanowione procesu rejestracji, zgodnie z którymi użytkownicy mogą zarejestrować swoje nazwy użytkownika i skojarzyć je z wystawionej samodzielnie klucze publiczne RSA.  
  
## <a name="client-credentials"></a>Poświadczenia klienta  
 Poświadczenia klienta są używane do uwierzytelniania klienta do usług w przypadkach, gdy jest wymagane uwierzytelnianie wzajemne. Sekcji można użyć do określenia usługi certyfikatów w scenariuszach, gdzie klient musi Zabezpieczanie komunikatów do usługi za pomocą certyfikatu usługi.  
  
 Można także skonfigurować klienta w ramach scenariusza z Federacją kompletną do użycia wystawione tokeny z bezpiecznego usługi tokenu lub lokalnego wystawcy tokenów. Aby uzyskać więcej informacji o scenariuszach obejmujących Federację, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Wszystkie poświadczenia klienta znajdują się w obszarze [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak pokazano w poniższym kodzie.  
  
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
  
#### <a name="clientcertifictate-element"></a>\<clientCertifictate > — Element  
 Ustawić certyfikat używany do uwierzytelniania klienta z tym elementem. Aby uzyskać więcej informacji, zobacz [porady: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Ta funkcja musi być włączona w usłudze Active Directory w systemach Windows i usługi Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken > — Element  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) zawiera elementy umożliwia konfigurowanie lokalnego wystawcy tokenów lub zachowania używane z usługi tokenu zabezpieczającego. Aby uzyskać instrukcje dotyczące konfigurowania klienta do używania wystawcy lokalnego, zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Określa domyślny adres usługi tokenu zabezpieczeń. Ten element jest używany podczas <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adres URL dla usługi tokenu zabezpieczającego lub gdy jest adres wystawcy wiązania federacyjnego http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous lub `null`. W takich przypadkach <xref:System.ServiceModel.Description.ClientCredentials> musi być skonfigurowany adres wystawcy lokalnego i powiązania, które używają do komunikowania się z tym wystawcą.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors >  
 Użyj [ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) funkcjonalności klienta WCF używany podczas komunikacji z usługi tokenu zabezpieczającego. Definiowanie zachowania klienta w [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) sekcji. Aby użyć zdefiniowanego zachowania, Dodaj <`add`> elementu `<issuerChannelBehaviors>` elementu o dwa atrybuty. Ustaw `issuerAddress` do adresu URL usługi tokenu zabezpieczeń i zestaw `behaviorConfiguration` atrybutu nazwy zachowanie określonych punktów końcowych, jak pokazano w poniższym przykładzie.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > — Element  
 Użyj tego elementu do kontrolowania uwierzytelniania certyfikatów usługi.  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) elementu można przechowywać jeden certyfikat używany, gdy usługa określa żadnego certyfikatu.  
  
 Użyj [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) i [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) można ustawić certyfikatów usługi, które są skojarzone z określonych usług. `<add>` Element zawiera `targetUri` atrybut, który jest używany do skojarzenia z usługą certyfikatu.  
  
 [ \<Uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element określa poziom zaufania używany do uwierzytelniania certyfikatów. Domyślnie "ChainTrust", który określa, że każdy certyfikat musi zostać znaleziony w hierarchii kończy się za zaufany urząd certyfikacji w górnej części łańcucha certyfikatów po ustawieniu poziomu. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość "PeerOrChainTrust", która określa, że certyfikaty wystawionej samodzielnie (relacja zaufania elementów równorzędnych) są akceptowane, a także certyfikaty, które znajdują się w łańcuchu zaufanego. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawione certyfikaty nie muszą można zakupić z zaufanego urzędu. Podczas wdrażania klienta, należy użyć wartości "ChainTrust". Można również ustawić wartość "Custom" lub "None." Aby użyć wartości "Custom", należy także ustawić `CustomCertificateValidatorType` atrybutu zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własnego niestandardowego modułu weryfikacji, musi dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi korzystającej z niestandardowego moduł weryfikacji certyfikatów](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [ \<Uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element zawiera `RevocationMode` atrybut określający, jak certyfikaty są sprawdzane pod kątem odwołań. Wartość domyślna to "online", co oznacza, że certyfikaty są automatycznie sprawdzane pod kątem odwołań. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) element zawiera elementy, które mają wpływ na autoryzacji, dostawców niestandardowej roli zabezpieczeń i personifikacji.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Klasy jest stosowany do metody usługi. Ten atrybut określa grupy użytkowników do użycia podczas nadanie Metoda chroniona. Wartością domyślną jest "UseWindowsGroups" i określa, czy grupy systemu Windows, takich jak "Administratorzy" lub "Użytkownicy", przeszukiwane są próby uzyskania dostępu do zasobu tożsamości. Można również określić "UseAspNetRoles" do używania dostawcy niestandardowej roli zabezpieczeń, który jest skonfigurowany w obszarze <`system.web` > element, jak pokazano w poniższym kodzie.  
  
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
 Użyj [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) do określenia zapisywane w dzienniku, a co typy dziennika zdarzeń. Aby uzyskać więcej informacji, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
 Eksportowanie metadanych do klientów jest wygodny dla deweloperów usługi i klienta, jak umożliwia pobieranie kodu konfiguracji i klienta. Aby zmniejszyć ryzyko usługi złośliwych użytkowników, jest możliwe do zabezpieczenia przy użyciu protokołu SSL za pośrednictwem protokołu HTTP (HTTPS) mechanizm transferu. Aby to zrobić, należy najpierw powiązać odpowiedniego certyfikatu X.509 określonego portu na komputerze, na którym uruchomiono usługę. (Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Po drugie, Dodaj [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) konfigurację usługi i zestawu `HttpsGetEnabled` atrybutu `true`. Wreszcie, ustaw `HttpsGetUrl` atrybutu na adres URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
