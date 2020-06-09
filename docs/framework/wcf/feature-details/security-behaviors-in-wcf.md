---
title: Zachowania zabezpieczeń w programie WCF
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: b25d476e9c9b4a70834274c6970dad1b056cecb9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595209"
---
# <a name="security-behaviors-in-wcf"></a>Zachowania zabezpieczeń w programie WCF
W Windows Communication Foundation (WCF), zachowania modyfikują zachowanie w czasie wykonywania na poziomie usługi lub na poziomie punktu końcowego. (Aby uzyskać więcej informacji na temat zachowań ogólnie, zobacz [Określanie zachowania usługi w czasie wykonywania](../specifying-service-run-time-behavior.md)). *Zachowania zabezpieczeń* umożliwiają kontrolę nad poświadczeniami, uwierzytelnianiem, autoryzacją i dziennikami inspekcji. Można używać zachowań przez programowanie lub przez konfigurację. Ten temat koncentruje się na konfigurowaniu następujących zachowań związanych z funkcjami zabezpieczeń:  
  
- [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).  
  
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).  
  
- [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
- [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md), co pozwala także określić bezpieczny punkt końcowy, do którego klienci mogą uzyskać dostęp do metadanych.  
  
## <a name="setting-credentials-with-behaviors"></a>Ustawianie poświadczeń przy użyciu zachowań  
 Użyj [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) i, [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) Aby ustawić wartości poświadczeń dla usługi lub klienta. Podstawowa konfiguracja powiązania określa, czy należy ustawić poświadczenie. Jeśli na przykład tryb zabezpieczeń jest ustawiony na `None` , zarówno klienci, jak i usługi nie uwierzytelniają się nawzajem i nie wymagają poświadczeń dowolnego typu.  
  
 Z drugiej strony powiązanie usługi może wymagać typu poświadczeń klienta. W takim przypadku może być konieczne ustawienie wartości poświadczeń przy użyciu zachowania. (Aby uzyskać więcej informacji na temat możliwych typów poświadczeń, zobacz [Wybieranie typu poświadczeń](selecting-a-credential-type.md)). W niektórych przypadkach, na przykład gdy poświadczenia systemu Windows są używane do uwierzytelniania, środowisko automatycznie ustala rzeczywistą wartość poświadczeń i nie trzeba jawnie ustawiać wartości poświadczeń (chyba że chcesz określić inny zestaw poświadczeń).  
  
 Wszystkie poświadczenia usługi są dostępne jako elementy podrzędne [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) . Poniższy przykład przedstawia certyfikat używany jako poświadczenie usługi.  
  
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
 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)Zawiera cztery elementy podrzędne. Elementy i ich zastosowania zostały omówione w poniższych sekcjach.  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Użyj tego elementu, aby określić certyfikat X. 509, który jest używany do uwierzytelniania usługi na klientach przy użyciu trybu zabezpieczeń wiadomości. Jeśli używasz certyfikatu, który okresowo odnawia, jego odcisk palca zmieni się. W takim przypadku należy użyć nazwy podmiotu jako `X509FindType` ponieważ certyfikat można wydać ponownie z tą samą nazwą podmiotu.  
  
 Aby uzyskać więcej informacji na temat korzystania z elementu, zobacz [How to: Określanie wartości poświadczeń klienta](../how-to-specify-client-credential-values.md).  
  
### <a name="certificate-of-clientcertificate-element"></a>\<certificate>\<clientCertificate>elementu  
 Użyj [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) elementu, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem, aby bezpiecznie komunikować się z klientem. Dzieje się tak w przypadku używania wzorca komunikacji dupleksowej. W wzorcu "żądanie-odpowiedź" Klient zawiera swój certyfikat w żądaniu, którego usługa używa do zabezpieczenia odpowiedzi z powrotem do klienta. Wzorzec komunikacji dupleksowej nie ma jednak żądań i odpowiedzi. Usługa nie może wywnioskować certyfikatu klienta z komunikacji i w związku z tym usługa wymaga certyfikatu klienta z wyprzedzeniem w celu zabezpieczenia komunikatów na kliencie. Należy uzyskać certyfikat klienta w sposób poza pasmem i określić certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usług dupleksowych, zobacz [How to: Create a Duplex kontraktu](how-to-create-a-duplex-contract.md).  
  
### <a name="authentication-of-clientcertificate-element"></a>\<authentication>\<clientCertificate>elementu  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)Element umożliwia dostosowanie sposobu uwierzytelniania klientów. Można ustawić `CertificateValidationMode` atrybut na `None` , `ChainTrust` ,,, `PeerOrChainTrust` `PeerTrust` lub `Custom` . Domyślnie poziom jest ustawiony na `ChainTrust` , który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się w *urzędzie głównym* w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość na `PeerOrChainTrust` , która określa, że certyfikaty samodzielne (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu. Podczas wdrażania klienta należy `ChainTrust` zamiast tego użyć wartości. Możesz również ustawić wartość na `Custom` . W przypadku ustawienia `Custom` wartości należy również ustawić `CustomCertificateValidatorType` atrybut na zestaw i typ używany do weryfikacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> .  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication> Element  
 Scenariusz wystawionego tokenu ma trzy etapy. Na pierwszym etapie klient próbujący uzyskać dostęp do usługi jest nazywany *usługą bezpiecznego tokenu* (STS). Następnie usługa STS uwierzytelnia klienta, a następnie wystawia klientowi token, zwykle tokena "Security Assertions Markup Language" (SAML). Klient następnie wraca do usługi przy użyciu tokenu. Usługa bada token dla danych, które umożliwiają usłudze uwierzytelnianie tokenu i w związku z tym klienta. Aby uwierzytelnić token, certyfikat, którego używa usługa bezpiecznego tokenu, musi być znany usłudze. [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)Element jest repozytorium dla wszystkich takich certyfikatów usługi Secure Token Service. Aby dodać certyfikaty, użyj [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) . Wstaw [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) dla każdego certyfikatu, jak pokazano w poniższym przykładzie.  
  
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
  
 Należy użyć [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) kolekcji w aplikacji federacyjnej, która używa *usługi bezpiecznego tokenu* (STS), która wystawia `SamlSecurityToken` tokeny zabezpieczające. Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie `SamlAudienceRestrictionCondition` do tokenu zabezpieczającego. Dzięki temu `SamlSecurityTokenAuthenticator` Usługa sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:  
  
- Ustaw `audienceUriMode` atrybut [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) na `Always` lub `BearerKeyOnly` .  
  
- Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji. W tym celu Wstaw [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) dla każdego identyfikatora URI  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [How to: Configure Credentials in a usługa federacyjna](how-to-configure-credentials-on-a-federation-service.md).  
  
#### <a name="allowing-anonymous-cardspace-users"></a>Zezwalanie anonimowym użytkownikom CardSpace  
 Ustawienie `AllowUntrustedRsaIssuers` atrybutu `<IssuedTokenAuthentication>` elementu `true` jawnie zezwala każdemu klientowi na prezentowanie samodzielnie wystawionego tokenu podpisanego za pomocą dowolnej pary kluczy RSA. Wystawca nie jest *zaufany* , ponieważ klucz nie ma skojarzonych z nim danych wystawcy. Użytkownik programu CardSpace może utworzyć kartę wystawioną automatycznie, która zawiera własne oświadczenia tożsamości. Użyj tej funkcji, aby zachować ostrożność. Aby użyć tej funkcji, należy traktować klucz publiczny RSA jako bezpieczniejsze hasło, które powinno być przechowywane w bazie danych wraz z nazwą użytkownika. Przed zezwoleniem na dostęp klienta do usługi, sprawdź, czy klucz publiczny RSA został przedstawiony przez klienta, porównując go z zapisanym kluczem publicznym dla prezentowanej nazwy użytkownika. Oznacza to, że został utworzony proces rejestracji, w którym użytkownicy mogą rejestrować nazwy użytkowników i kojarzyć je z wystawionymi przez siebie kluczami publicznymi RSA.  
  
## <a name="client-credentials"></a>Poświadczenia klienta  
 Poświadczenia klienta służą do uwierzytelniania klienta programu w przypadku, gdy wymagane jest uwierzytelnianie wzajemne. Za pomocą tej sekcji można określić certyfikaty usługi dla scenariuszy, w których klient musi zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.  
  
 Możesz również skonfigurować klienta jako część scenariusza federacyjnego, aby użyć wystawionych tokenów z usługi bezpiecznego tokenu lub lokalnego wystawcy tokenów. Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [federacyjnego i wystawione tokeny](federation-and-issued-tokens.md). Wszystkie poświadczenia klienta znajdują się w [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) , jak pokazano w poniższym kodzie.  
  
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
 Ustaw certyfikat używany do uwierzytelniania klienta przy użyciu tego elementu. Aby uzyskać więcej informacji, zobacz [How to: Określanie wartości poświadczeń klienta](../how-to-specify-client-credential-values.md).  
  
#### \<httpDigest>  
 Ta funkcja musi być włączona z Active Directory w systemie Windows i Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).  
  
#### <a name="issuedtoken-element"></a>\<issuedToken> Element  
 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md)Zawiera elementy służące do konfigurowania lokalnego wystawcy tokenów lub zachowań używanych z usługą tokenu zabezpieczającego. Aby uzyskać instrukcje dotyczące konfigurowania klienta do korzystania z wystawcy lokalnego, zobacz [How to: Configure a Local wystawca](how-to-configure-a-local-issuer.md).  
  
#### \<localIssuerAddress>  
 Określa domyślny adres usługi tokenu zabezpieczającego. Ta wartość jest używana, gdy <xref:System.ServiceModel.WSFederationHttpBinding> program nie poda adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego ma wartość `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null` . W takich przypadkach <xref:System.ServiceModel.Description.ClientCredentials> należy skonfigurować adres wystawcy lokalnego i powiązanie, które ma być używane do komunikacji z tym wystawcą.  
  
#### \<issuerChannelBehaviors>  
 Użyj, [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) Aby dodać zachowania klienta WCF używane podczas komunikowania się z usługą tokenu zabezpieczającego. Zdefiniuj zachowania klienta w [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) sekcji. Aby użyć zdefiniowanego zachowania, Dodaj element <`add`> do `<issuerChannelBehaviors>` elementu z dwoma atrybutami. Ustaw wartość `issuerAddress` na adres URL usługi tokenu zabezpieczającego i ustaw dla `behaviorConfiguration` atrybutu nazwę zachowania zdefiniowanego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
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
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate> Element  
 Ten element służy do kontrolowania uwierzytelniania certyfikatów usług.  
  
 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md)Element może przechowywać pojedynczy certyfikat używany, gdy usługa nie określa certyfikatu.  
  
 Użyj [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) i, [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) Aby ustawić certyfikaty usług, które są skojarzone z określonymi usługami. `<add>`Element zawiera `targetUri` atrybut, który jest używany do kojarzenia certyfikatu z usługą.  
  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)Element określa poziom zaufania używany do uwierzytelniania certyfikatów. Domyślnie poziom jest ustawiony na wartość "ChainTrust", co oznacza, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się w zaufanym urzędzie certyfikacji w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość "PeerOrChainTrust", która określa, że certyfikaty wystawione przez siebie (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu. Podczas wdrażania klienta należy zamiast tego użyć wartości "ChainTrust". Możesz również ustawić wartość na "Custom" lub "none" (brak). Aby użyć wartości "Custom", należy również ustawić `CustomCertificateValidatorType` atrybut na zestaw i typ używany do walidacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Aby uzyskać więcej informacji, zobacz [How to: Create a Service, która korzysta z niestandardowego modułu weryfikacji certyfikatu](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)Element zawiera `RevocationMode` atrybut, który określa sposób sprawdzania certyfikatów do odwołania. Wartość domyślna to "online", co oznacza, że certyfikaty są automatycznie sprawdzane pod kątem odwołania. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](working-with-certificates.md).  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)Element zawiera elementy, które mają wpływ na autoryzację, niestandardowych dostawców ról i personifikację.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>Klasa jest stosowana do metody usługi. Ten atrybut określa grupy użytkowników do użycia podczas autoryzowania używania metody chronionej. Wartość domyślna to "UseWindowsGroups" i określa, że grupy systemu Windows, takie jak "Administratorzy" lub "Użytkownicy", są wyszukiwane pod kątem tożsamości próbującej uzyskać dostęp do zasobu. Możesz również określić wartość "UseAspNetRoles", aby użyć niestandardowego dostawcy ról, który jest skonfigurowany w <`system.web` > elementu, jak pokazano w poniższym kodzie.  
  
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
  
 Poniższy kod przedstawia `roleProviderName` użycie `principalPermissionMode` atrybutu.  
  
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
 Użyj, [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) Aby określić dziennik zapisany w i typy zdarzeń do zarejestrowania. Aby uzyskać więcej informacji, zobacz [Inspekcja](auditing-security-events.md).  
  
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
 Eksportowanie metadanych do klientów jest wygodne w przypadku deweloperów usług i klientów, ponieważ umożliwia pobieranie konfiguracji i kodu klienta. Aby zmniejszyć narażenie usługi na złośliwych użytkowników, można zabezpieczyć transfer przy użyciu mechanizmu protokołu SSL przez HTTP (HTTPS). W tym celu należy najpierw powiązać odpowiedni certyfikat X. 509 z określonym portem na komputerze hostującym usługę. (Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](working-with-certificates.md).) Następnie należy dodać [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) do konfiguracji usługi i ustawić `HttpsGetEnabled` atrybut na `true` . Na koniec Ustaw `HttpsGetUrl` atrybut na adres URL punktu końcowego metadanych usługi, jak pokazano w poniższym przykładzie.  
  
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

- [Inspekcja](auditing-security-events.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
