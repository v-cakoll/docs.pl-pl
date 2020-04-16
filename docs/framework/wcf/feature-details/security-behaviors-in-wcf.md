---
title: Zachowania zabezpieczeń w programie WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 9f96abac0f5f32279c5579dd01c3dd7f2dc1786c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464046"
---
# <a name="security-behaviors-in-wcf"></a>Zachowania zabezpieczeń w programie WCF
W programie Windows Communication Foundation (WCF) zachowania modyfikują zachowanie w czasie wykonywania na poziomie usługi lub na poziomie punktu końcowego. (Aby uzyskać więcej informacji na temat zachowań w ogóle, zobacz [Określanie zachowania w czasie wykonywania usługi](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md).) *Zachowania zabezpieczeń* umożliwiają kontrolę nad poświadczeniami, uwierzytelnianiem, autoryzacją i inspekcją dzienników. Zachowania można używać przez programowanie lub konfigurację. W tym temacie skupiono się na konfigurowaniu następujących zachowań związanych z funkcjami zabezpieczeń:  
  
- serviceCredentials>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
- clientCredentials>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
- usługaZaadowywania>. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
- >serwissecurityaudit . [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
  
- serviceMetadata>, który umożliwia również określenie bezpiecznego punktu końcowego, do którego klienci mogą uzyskiwać dostęp do metadanych. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)  
  
## <a name="setting-credentials-with-behaviors"></a>Ustawianie poświadczeń za pomocą zachowań  
 Użyj [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) i [ \<clientCredentials>,](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) aby ustawić wartości poświadczeń dla usługi lub klienta. Podstawowa konfiguracja powiązania określa, czy poświadczenia ma być ustawiona. Na przykład jeśli tryb zabezpieczeń `None`jest ustawiony na , zarówno klienci, jak i usługi nie uwierzytelniają się nawzajem i nie wymagają żadnych poświadczeń dowolnego typu.  
  
 Z drugiej strony powiązanie usługi może wymagać typu poświadczeń klienta. W takim przypadku może być wymagane ustawienie wartości poświadczeń przy użyciu zachowania. (Aby uzyskać więcej informacji na temat możliwych typów poświadczeń, zobacz [Wybieranie typu poświadczeń.](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md) W niektórych przypadkach, na przykład gdy poświadczenia systemu Windows są używane do uwierzytelniania, środowisko automatycznie ustanawia rzeczywistą wartość poświadczeń i nie trzeba jawnie ustawić wartość poświadczeń (chyba że chcesz określić inny zestaw poświadczeń).  
  
 Wszystkie poświadczenia usługi znajdują się jako elementy podrzędne [ \<usługiZachowa>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). W poniższym przykładzie pokazano certyfikat używany jako poświadczenie usługi.  
  
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
 [ \<ServiceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) zawiera cztery elementy podrzędne. Elementy i ich użycia są omówione w poniższych sekcjach.  
  
### <a name="servicecertificate-element"></a>\<serviceCertyfikat> Element  
 Ten element służy do określania certyfikatu X.509 używanego do uwierzytelniania usługi klientom przy użyciu trybu zabezpieczeń wiadomości. Jeśli używasz certyfikatu, który jest okresowo odnawiany, zmienia się jego odcisk palca. W takim przypadku należy użyć `X509FindType` nazwy podmiotu jako, ponieważ certyfikat może zostać ponownie wydany o tej samej nazwie podmiotu.  
  
 Aby uzyskać więcej informacji na temat korzystania z elementu, zobacz [Jak: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certyfikat> \<klientaKertyfikacyjny> Element  
 Użyj [ \<elementu>certyfikatu,](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) gdy usługa musi mieć certyfikat klienta z wyprzedzeniem, aby bezpiecznie komunikować się z klientem. Dzieje się tak podczas korzystania z wzorca komunikacji dupleksowej. W bardziej typowy pattern żądanie odpowiedź klient zawiera jego certyfikat w żądaniu, który usługa używa do zabezpieczenia jego odpowiedzi z powrotem do klienta. Wzorzec komunikacji dupleksowej nie ma jednak żadnych żądań i odpowiedzi. Usługa nie może wywnioskować certyfikat klienta z komunikacji i dlatego usługa wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomości do klienta. Certyfikat klienta należy uzyskać w sposób poza pasmem i określić certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usług dupleksu, zobacz [Jak: Tworzenie kontraktu dupleksowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<> uwierzytelniania \<elementu> certyfikatu klienta  
 Element [ \<>uwierzytelniania](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) umożliwia dostosowanie sposobu uwierzytelniania klientów. Można ustawić `CertificateValidationMode` atrybut na `None` `ChainTrust`, `PeerOrChainTrust` `PeerTrust`, `Custom`, , lub . Domyślnie poziom jest ustawiony `ChainTrust`na , który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się *w urzędzie głównym* u góry łańcucha. Jest to najbezpieczniejszy tryb. Można również ustawić wartość `PeerOrChainTrust`, która określa, że certyfikaty wystawiane samodzielnie (zaufanie równorzędne) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione samodzielnie nie muszą być kupowane od zaufanego urzędu. Podczas wdrażania klienta, należy `ChainTrust` użyć wartości zamiast tego. Można również ustawić wartość `Custom`na . Po ustawieniu `Custom` wartości należy również `CustomCertificateValidatorType` ustawić atrybut na zestaw i typ używany do sprawdzania poprawności certyfikatu. Aby utworzyć własny niestandardowy walidator, <xref:System.IdentityModel.Selectors.X509CertificateValidator> należy dziedziczyć z klasy abstrakcyjnej.  
  
### <a name="issuedtokenauthentication-element"></a>\<wydanaTokenAuthentication element>  
 Scenariusz wystawionego tokenu ma trzy etapy. W pierwszym etapie klient próbujący uzyskać dostęp do usługi jest określany do *usługi bezpiecznego tokenu* (STS). Sts następnie uwierzytelnia klienta, a następnie wystawia klientowi token, zazwyczaj token języka znaczników zabezpieczeń (SAML). Klient następnie zwraca do usługi z tokenem. Usługa sprawdza token dla danych, który umożliwia usługi uwierzytelnić token i w związku z tym klienta. Aby uwierzytelnić token, certyfikat używany przez usługę bezpiecznego tokenu musi być znany usłudze. Element [ \<>issuedTokenAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) jest repozytorium dla takich certyfikatów usługi bezpiecznego tokenu. Aby dodać certyfikaty, użyj [ \<znanego certyfikatów>](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Wstaw [ \<>dodawania](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Domyślnie certyfikaty muszą być uzyskane z usługi bezpiecznego tokenu. Te "znane" certyfikaty zapewniają, że tylko legalni klienci mogą uzyskać dostęp do usługi.  
  
 Należy użyć [ \<allowedAudienceUris>](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) kolekcji w aplikacji federacyjnej, która wykorzystuje usługę bezpiecznego `SamlSecurityToken` *tokenu* (STS), która wystawia tokeny zabezpieczające. Gdy STS wystawia token zabezpieczający, można określić identyfikator URI usług sieci Web, `SamlAudienceRestrictionCondition` dla których token zabezpieczający jest przeznaczony przez dodanie do tokenu zabezpieczającego. Dzięki temu `SamlSecurityTokenAuthenticator` usługa sieci Web adresata może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że ta kontrola powinna się odbyć, wykonując następujące czynności:  
  
- Ustaw `audienceUriMode` atrybut [ \<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) do `Always` lub `BearerKeyOnly`.  
  
- Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji. Aby to zrobić, wstaw [ \<>dodawania](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) dla każdego identyfikatora URI  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Jak: Konfigurowanie poświadczeń w usłudze federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Zezwalanie anonimowym użytkownikom CardSpace  
 Ustawienie `AllowUntrustedRsaIssuers` atrybutu `<IssuedTokenAuthentication>` elementu `true` jawnie umożliwia każdemu klientowi przedstawienie tokenu wystawionego samodzielnie podpisanego z dowolną parą kluczy RSA. Wystawca jest *niezaufany,* ponieważ klucz nie ma skojarzonych z nim danych wystawcy. Użytkownik CardSpace może utworzyć samodzielnie wystawioną kartę, która zawiera samodzielnie dostarczone oświadczenia o tożsamości. Użyj tej funkcji z ostrożnością. Aby użyć tej funkcji, należy myśleć o klucz publiczny RSA jako bardziej bezpieczne hasło, które powinny być przechowywane w bazie danych wraz z nazwą użytkownika. Przed zezwoleniem klientowi na dostęp do usługi należy zweryfikować klucz publiczny rsa przedstawiony przez klienta, porównując go z przechowywanym kluczem publicznym dla prezentowanej nazwy użytkownika. Zakłada to, że ustanowiono proces rejestracji, w którym użytkownicy mogą rejestrować swoje nazwy użytkowników i kojarzyć je z samodzielnie wystawionymi kluczami publicznymi RSA.  
  
## <a name="client-credentials"></a>Poświadczenia klienta  
 Poświadczenia klienta są używane do uwierzytelniania klienta do usług w przypadkach, gdy wymagane jest wzajemne uwierzytelnianie. Za pomocą tej sekcji można określić certyfikaty usług dla scenariuszy, w których klient musi zabezpieczyć wiadomości do usługi z certyfikatem usługi.  
  
 Można również skonfigurować klienta jako część scenariusza federacji, aby używać wystawionych tokenów z usługi bezpiecznego tokenu lub lokalnego wystawcy tokenów. Aby uzyskać więcej informacji na temat scenariuszy federacyjnego, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). Wszystkie poświadczenia klienta znajdują się w [ \<ramach endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md), jak pokazano w poniższym kodzie.  
  
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
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a>\<clientCertificate> Element  
 Ustaw certyfikat używany do uwierzytelniania klienta za pomocą tego elementu. Aby uzyskać więcej informacji, zobacz [Jak: Określanie wartości poświadczeń klienta](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 Ta funkcja musi być włączona w usłudze Active Directory w systemie Windows i internetowych usługach informacyjnych (IIS). Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie szyfrowane w iIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<wydanyDochoń> Element  
 [ \<>issuedToken](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) zawiera elementy używane do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego. Aby uzyskać instrukcje dotyczące konfigurowania klienta do używania wystawcy lokalnego, zobacz [Jak: Konfigurowanie wystawcy lokalnego](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 Określa domyślny adres usługi tokenu zabezpieczającego. Jest to używane, gdy <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adresu URL dla usługi tokenu zabezpieczającego lub `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`gdy adres wystawcy powiązania federacyjnego jest lub . W takich przypadkach <xref:System.ServiceModel.Description.ClientCredentials> musi być skonfigurowany z adresem lokalnego emitenta i powiązanie do użycia do komunikowania się z tym wystawcą.  
  
#### <a name="issuerchannelbehaviors"></a>\<>  
 Użyj [ \<issuerChannelBehaviors>,](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) aby dodać zachowania klientów WCF używane podczas komunikowania się z usługą tokenu zabezpieczającego. Zdefiniuj zachowania klienta w [ \<sekcji endpointBehaviors>.](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) Aby użyć zdefiniowanego zachowania, dodaj `add` <> element do `<issuerChannelBehaviors>` elementu z dwoma atrybutami. `issuerAddress` Ustaw adres URL usługi tokenu zabezpieczającego `behaviorConfiguration` i ustaw atrybut na nazwę zdefiniowanego zachowania punktu końcowego, jak pokazano w poniższym przykładzie.  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertyfikat> Element  
 Ten element służy do kontrolowania uwierzytelniania certyfikatów usługi.  
  
 Element [ \<>defaultCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) może przechowywać pojedynczy certyfikat używany, gdy usługa nie określa certyfikatu.  
  
 Użyj [ \<scopedCertificates>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) i [ \<dodaj>,](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) aby ustawić certyfikaty usług, które są skojarzone z określonymi usługami. Element `<add>` zawiera `targetUri` atrybut, który jest używany do skojarzenia certyfikatu z usługą.  
  
 Element [ \<>uwierzytelniania](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) określa poziom zaufania używany do uwierzytelniania certyfikatów. Domyślnie poziom jest ustawiony na "ChainTrust", który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się w zaufanym urzędzie certyfikacji u góry łańcucha. Jest to najbezpieczniejszy tryb. Można również ustawić wartość "PeerOrChainTrust", która określa, że certyfikaty wystawiane samodzielnie (zaufanie równorzędne) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione samodzielnie nie muszą być kupowane od zaufanego urzędu. Podczas wdrażania klienta należy użyć wartości "ChainTrust". Można również ustawić wartość na "Niestandardowe" lub "Brak". Aby użyć wartości "Niestandardowe", należy `CustomCertificateValidatorType` również ustawić atrybut na zestaw i typ używany do sprawdzania poprawności certyfikatu. Aby utworzyć własny niestandardowy walidator, <xref:System.IdentityModel.Selectors.X509CertificateValidator> należy dziedziczyć z klasy abstrakcyjnej. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie usługi, która zatrudnia niestandardowego walidatora certyfikatów](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Element [ \<>uwierzytelniania](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) zawiera `RevocationMode` atrybut, który określa sposób sprawdzania certyfikatów pod kątem odwołania. Wartość domyślna to "online", która wskazuje, że certyfikaty są automatycznie sprawdzane pod kątem odwołania. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>Autoryzacja usługi  
 [ \<ServiceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) element zawiera elementy, które wpływają na autoryzację, dostawców ról niestandardowych i personifikacji.  
  
 Klasa <xref:System.Security.Permissions.PrincipalPermissionAttribute> jest stosowana do metody usługi. Atrybut określa grupy użytkowników, których należy używać podczas autoryzowania użycia metody chronionej. Wartością domyślną jest "UseWindowsGroups" i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu. Można również określić "UseAspNetRoles", aby użyć niestandardowego dostawcy ról, `system.web` który jest skonfigurowany w <> element, jak pokazano w poniższym kodzie.  
  
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
  
 Poniższy kod `roleProviderName` przedstawia używane `principalPermissionMode` z atrybutem.  
  
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
 Użyj [ \<>serviceSecurityAudit,](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) aby określić dziennik zapisany do i jakie typy zdarzeń do zarejestrowania. Aby uzyskać więcej informacji, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```xml  
<behaviors>
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
 Eksportowanie metadanych do klientów jest wygodne dla deweloperów usług i klientów, ponieważ umożliwia pobieranie konfiguracji i kodu klienta. Aby zmniejszyć narażenie usługi na złośliwych użytkowników, możliwe jest zabezpieczenie transferu za pomocą mechanizmu SSL za pośrednictwem protokołu HTTP (HTTPS). Aby to zrobić, należy najpierw powiązać odpowiedni certyfikat X.509 z określonym portem na komputerze, na który jest obsługiwany serwis. (Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Po drugie dodaj [ \<>serviceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do konfiguracji usługi `HttpsGetEnabled` i `true`ustaw atrybut na . Na koniec ustaw `HttpsGetUrl` atrybut do adresu URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
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

- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
