---
title: Zachowania zabezpieczeń w programie WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 12ae9bb90752fe3ee76404948693c501fc42efe6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730945"
---
# <a name="security-behaviors-in-wcf"></a>Zachowania zabezpieczeń w programie WCF
W Windows Communication Foundation (WCF), zachowania modyfikują zachowanie w czasie wykonywania na poziomie usługi lub na poziomie punktu końcowego. (Aby uzyskać więcej informacji na temat zachowań ogólnie, zobacz [Określanie zachowania usługi w czasie wykonywania](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)). *Zachowania zabezpieczeń* umożliwiają kontrolę nad poświadczeniami, uwierzytelnianiem, autoryzacją i dziennikami inspekcji. Można używać zachowań przez programowanie lub przez konfigurację. Ten temat koncentruje się na konfigurowaniu następujących zachowań związanych z funkcjami zabezpieczeń:  
  
- [>\<ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<obiekt clientcredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<> ServiceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<> metadanych](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md), co umożliwia również określenie bezpiecznego punktu końcowego, do którego klienci mogą uzyskać dostęp do metadanych.  
  
## <a name="setting-credentials-with-behaviors"></a>Ustawianie poświadczeń przy użyciu zachowań  
 Użyj [\<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) i [\<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) , aby ustawić wartości poświadczeń dla usługi lub klienta. Podstawowa konfiguracja powiązania określa, czy należy ustawić poświadczenie. Na przykład, jeśli tryb zabezpieczeń jest ustawiony na `None`, zarówno klienci, jak i usługi nie uwierzytelniają się nawzajem i nie wymagają poświadczeń dowolnego typu.  
  
 Z drugiej strony powiązanie usługi może wymagać typu poświadczeń klienta. W takim przypadku może być konieczne ustawienie wartości poświadczeń przy użyciu zachowania. (Aby uzyskać więcej informacji na temat możliwych typów poświadczeń, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)). W niektórych przypadkach, na przykład gdy poświadczenia systemu Windows są używane do uwierzytelniania, środowisko automatycznie ustala rzeczywistą wartość poświadczeń i nie trzeba jawnie ustawiać wartości poświadczeń (chyba że chcesz określić inny zestaw poświadczeń).  
  
 Wszystkie poświadczenia usługi są dostępne jako elementy podrzędne [\<> serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Poniższy przykład przedstawia certyfikat używany jako poświadczenie usługi.  
  
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
 [\<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zawiera cztery elementy podrzędne. Elementy i ich zastosowania zostały omówione w poniższych sekcjach.  
  
### <a name="servicecertificate-element"></a>\<elementu > serviceCertificate  
 Użyj tego elementu, aby określić certyfikat X. 509, który jest używany do uwierzytelniania usługi na klientach przy użyciu trybu zabezpieczeń wiadomości. Jeśli używasz certyfikatu, który okresowo odnawia, jego odcisk palca zmieni się. W takim przypadku użyj nazwy podmiotu jako `X509FindType`, ponieważ można ponownie wydać certyfikat z tą samą nazwą podmiotu.  
  
 Aby uzyskać więcej informacji na temat korzystania z elementu, zobacz [How to: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<> certyfikatu \<elementu > clientCertificate  
 Użyj [\<certyfikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) elementu, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem, aby bezpiecznie komunikować się z klientem. Dzieje się tak w przypadku używania wzorca komunikacji dupleksowej. W wzorcu "żądanie-odpowiedź" Klient zawiera swój certyfikat w żądaniu, którego usługa używa do zabezpieczenia odpowiedzi z powrotem do klienta. Wzorzec komunikacji dupleksowej nie ma jednak żądań i odpowiedzi. Usługa nie może wywnioskować certyfikatu klienta z komunikacji i w związku z tym usługa wymaga certyfikatu klienta z wyprzedzeniem w celu zabezpieczenia komunikatów na kliencie. Należy uzyskać certyfikat klienta w sposób poza pasmem i określić certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usług dupleksowych, zobacz [How to: Create a Duplex kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>> \<uwierzytelniania \<clientCertificate > elementu  
 Element [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) umożliwia dostosowanie sposobu uwierzytelniania klientów. Można ustawić atrybut `CertificateValidationMode` na `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`lub `Custom`. Domyślnie poziom jest ustawiany na `ChainTrust`, który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się w *urzędzie głównym* w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Możesz również ustawić wartość `PeerOrChainTrust`, która określa, że certyfikaty samodzielne (zaufanie równorzędne) są akceptowane, a także certyfikaty znajdujące się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu. Podczas wdrażania klienta należy zamiast tego użyć wartości `ChainTrust`. Możesz również ustawić wartość `Custom`. Po ustawieniu wartości `Custom` należy również ustawić atrybut `CustomCertificateValidatorType` na zestaw i typ używany do weryfikacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
### <a name="issuedtokenauthentication-element"></a>\<element > issuedTokenAuthentication  
 Scenariusz wystawionego tokenu ma trzy etapy. Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu* (STS). Następnie usługa STS uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML). Klient następnie wraca do usługi przy użyciu tokenu. Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta. Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze. Element [\<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. Aby dodać certyfikaty, użyj [\<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [\<dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Domyślnie certyfikaty muszą być uzyskiwane z usługi bezpiecznego tokenu. Te "znane" certyfikaty zapewniają dostęp do usługi tylko uprawnionym klientom.  
  
 Należy użyć kolekcji [\<allowedAudienceUris >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) w aplikacji federacyjnej, która wykorzystuje *usługę Secure Token Service* (STS), która wystawia `SamlSecurityToken` tokeny zabezpieczające. Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie `SamlAudienceRestrictionCondition` do tokenu zabezpieczającego. Dzięki temu `SamlSecurityTokenAuthenticator` dla usługi sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:  
  
- Ustaw atrybut `audienceUriMode` [\<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) na `Always` lub `BearerKeyOnly`.  
  
- Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji. Aby to zrobić, Wstaw [\<dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) dla każdego identyfikatora URI  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [How to: Configure Credentials in a usługa federacyjna](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Zezwalanie anonimowym użytkownikom CardSpace  
 Ustawienie atrybutu `AllowUntrustedRsaIssuers` elementu `<IssuedTokenAuthentication>` w taki sposób, aby `true` jawnie zezwolił klientowi na prezentowanie tokenów wystawionych samodzielnie z dowolną parą kluczy RSA. Wystawca nie jest *zaufany* , ponieważ klucz nie ma skojarzonych z nim danych wystawcy. Użytkownik programu CardSpace może utworzyć kartę wystawioną automatycznie, która zawiera własne oświadczenia tożsamości. Użyj tej funkcji, aby zachować ostrożność. Aby użyć tej funkcji, należy traktować klucz publiczny RSA jako bezpieczniejsze hasło, które powinno być przechowywane w bazie danych wraz z nazwą użytkownika. Przed zezwoleniem na dostęp klienta do usługi, sprawdź, czy klucz publiczny RSA został przedstawiony przez klienta, porównując go z zapisanym kluczem publicznym dla prezentowanej nazwy użytkownika. Oznacza to, że został utworzony proces rejestracji, w którym użytkownicy mogą rejestrować nazwy użytkowników i kojarzyć je z wystawionymi przez siebie kluczami publicznymi RSA.  
  
## <a name="client-credentials"></a>Poświadczenia klienta  
 Poświadczenia klienta służą do uwierzytelniania klienta programu w przypadku, gdy wymagane jest uwierzytelnianie wzajemne. Za pomocą tej sekcji można określić certyfikaty usługi dla scenariuszy, w których klient musi zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.  
  
 Możesz również skonfigurować klienta jako część scenariusza federacyjnego, aby użyć wystawionych tokenów z usługi bezpiecznego tokenu lub lokalnego wystawcy tokenów. Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Wszystkie poświadczenia klienta znajdują się w [\<> endpointBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak pokazano w poniższym kodzie.  
  
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
  
#### <a name="clientcertificate-element"></a>\<clientCertificate > element  
 Ustaw certyfikat używany do uwierzytelniania klienta przy użyciu tego elementu. Aby uzyskać więcej informacji, zobacz [How to: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest >  
 Ta funkcja musi być włączona z Active Directory w systemie Windows i Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<element > issuedToken  
 [\<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) zawiera elementy służące do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego. Aby uzyskać instrukcje dotyczące konfigurowania klienta do korzystania z wystawcy lokalnego, zobacz [How to: Configure a Local wystawca](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress >  
 Określa domyślny adres usługi tokenu zabezpieczającego. Ta wartość jest używana, gdy <xref:System.ServiceModel.WSFederationHttpBinding> nie poda adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego jest `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null`. W takich przypadkach <xref:System.ServiceModel.Description.ClientCredentials> musi być skonfigurowany przy użyciu adresu wystawcy lokalnego i powiązania, które ma być używane do komunikacji z tym wystawcą.  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors >  
 Użyj [\<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) , aby dodać zachowania klienta WCF używane podczas komunikowania się z usługą tokenu zabezpieczającego. Zdefiniuj zachowania klienta w sekcji [\<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) . Aby użyć zdefiniowanego zachowania, należy dodać element <`add`> do elementu `<issuerChannelBehaviors>` z dwoma atrybutami. Ustaw `issuerAddress` na adres URL usługi tokenów zabezpieczających i ustaw atrybut `behaviorConfiguration` na nazwę zachowania zdefiniowanego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<elementu > serviceCertificate  
 Ten element służy do kontrolowania uwierzytelniania certyfikatów usług.  
  
 Element [\<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) może przechowywać pojedynczy certyfikat używany, gdy usługa nie będzie określać certyfikatu.  
  
 Użyj [\<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) i [\<dodać >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) , aby ustawić certyfikaty usług, które są skojarzone z określonymi usługami. Element `<add>` zawiera atrybut `targetUri`, który jest używany do kojarzenia certyfikatu z usługą.  
  
 [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) określa poziom zaufania używany do uwierzytelniania certyfikatów. Domyślnie poziom jest ustawiony na wartość "ChainTrust", co oznacza, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się w zaufanym urzędzie certyfikacji w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość "PeerOrChainTrust", która określa, że certyfikaty wystawione przez siebie (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu. Podczas wdrażania klienta należy zamiast tego użyć wartości "ChainTrust". Możesz również ustawić wartość na "Custom" lub "none" (brak). Aby użyć wartości "Custom", należy również ustawić atrybut `CustomCertificateValidatorType` na zestaw i typ używany do walidacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Aby uzyskać więcej informacji, zobacz [How to: Create a Service, która korzysta z niestandardowego modułu weryfikacji certyfikatu](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Element [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) zawiera atrybut `RevocationMode`, który określa, jak certyfikaty są sprawdzane pod kątem odwołania. Wartość domyślna to "online", co oznacza, że certyfikaty są automatycznie sprawdzane pod kątem odwołania. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 Element [\<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) zawiera elementy, które mają wpływ na autoryzację, niestandardowych dostawców ról i personifikacji.  
  
 Klasa <xref:System.Security.Permissions.PrincipalPermissionAttribute> jest stosowana do metody usługi. Ten atrybut określa grupy użytkowników do użycia podczas autoryzowania używania metody chronionej. Wartość domyślna to "UseWindowsGroups" i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu. Można również określić wartość "UseAspNetRoles", aby użyć niestandardowego dostawcy ról, który jest skonfigurowany w <`system.web` > elementu, jak pokazano w poniższym kodzie.  
  
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
  
 Poniższy kod przedstawia `roleProviderName` używany z atrybutem `principalPermissionMode`.  
  
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
 Użyj [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) , aby określić dziennik zapisany w i typy zdarzeń do zarejestrowania. Aby uzyskać więcej informacji, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
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
  
## <a name="secure-metadata-exchange"></a>Bezpieczna wymiana metadanych  
 Eksportowanie metadanych do klientów jest wygodne w przypadku deweloperów usług i klientów, ponieważ umożliwia pobieranie konfiguracji i kodu klienta. Aby zmniejszyć narażenie usługi na złośliwych użytkowników, można zabezpieczyć transfer przy użyciu mechanizmu protokołu SSL przez HTTP (HTTPS). W tym celu należy najpierw powiązać odpowiedni certyfikat X. 509 z określonym portem na komputerze hostującym usługę. (Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Następnie Dodaj [>\<ServiceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do konfiguracji usługi i ustaw atrybut `HttpsGetEnabled` na `true`. Na koniec ustaw atrybut `HttpsGetUrl` na adres URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
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
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
