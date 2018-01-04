---
title: "Dostawca tokenów SAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7afdbcde68a811dd8fb2be84c1ae298496992c9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="saml-token-provider"></a>Dostawca tokenów SAML
W tym przykładzie pokazano, jak implementacja klienta niestandardowego dostawcy tokenu SAML. Dostawca tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do podawania poświadczeń w celu zabezpieczenia infrastruktury. Dostawca tokenu ogólnie sprawdza obiektu docelowego i problemów odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć komunikatu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jest dostarczany z domyślnym dostawcy tokenu Menedżera poświadczeń. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]również jest dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu. Tokenów niestandardowi są przydatne w następujących przypadkach:  
  
-   Jeśli masz Magazyn poświadczeń, które tych dostawców tokenu nie może pracować z.  
  
-   Jeśli chcesz udostępnić własny niestandardowy mechanizm do przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje o tym, kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta używa poświadczeń.  
  
-   Jeśli tworzysz niestandardowy token.  
  
 Ten przykład przedstawia sposób tworzenia niestandardowego dostawcę tokenów, który umożliwia tokenu SAML uzyskany poza [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta do użycia.  
  
 Krótko mówiąc, w tym przykładzie przedstawiono poniżej:  
  
-   Jak można skonfigurować klienta z niestandardowego dostawcy tokenu.  
  
-   Jak tokenu SAML mogą być przekazywane do poświadczeń klienta.  
  
-   Jak tokenu SAML są dostarczane do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta.  
  
-   Jak serwer jest uwierzytelniany przez klienta przy użyciu certyfikat X.509.  
  
 Usługa udostępnia dwa punkty końcowe komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z normą `wsFederationHttpBinding`, zabezpieczenia komunikatów, który używa. Jeden punkt końcowy oczekuje klienta do uwierzytelniania za pomocą tokenu SAML, który używa symetrycznego klucza poświadczającego, podczas gdy druga oczekuje klienta do uwierzytelniania za pomocą tokenu SAML, który używa klucza potwierdzającego asymetrycznego. Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie. `serviceCredentials` Zachowanie umożliwia konfigurowanie certyfikatu usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewnienia ochrony wiadomości. Następująca konfiguracja odwołuje się do certyfikatu "localhost" instalowane podczas instalacji próbki zgodnie z opisem w instrukcjach instalacji na końcu tego tematu. `serviceCredentials` Zachowanie umożliwia również konfigurowanie certyfikatów, które są zaufane do podpisywania tokenów SAML. Następująca konfiguracja odwołuje się do certyfikatu "Alicja" instalowane w ramach przykładu.  
  
```xml  
<system.serviceModel>  
 <services>  
  <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
   <host>  
    <baseAddresses>  
     <!-- configure base address provided by host -->  
     <add    
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />  
    </baseAddresses>  
   </host>  
   <!-- use base address provided by host -->  
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->  
   <endpoint address="calc/symm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->  
   <endpoint address="calc/asymm"  
             binding="wsFederationHttpBinding"  
             bindingConfiguration="Binding2"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
 </services>  
  
 <bindings>  
  <wsFederationHttpBinding>  
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->  
   <binding name="Binding1">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"   
              issuedKeyType="SymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>  
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->  
   <binding name="Binding2">  
    <security mode="Message">  
     <message negotiateServiceCredential ="false"  
              issuedKeyType="AsymmetricKey"   
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />  
    </security>  
   </binding>          
  </wsFederationHttpBinding>  
 </bindings>  
  
 <behaviors>  
  <serviceBehaviors>  
   <behavior name="CalculatorServiceBehavior">  
    <!--   
    The serviceCredentials behavior allows one to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
    This configuration references the "localhost" certificate installed during the setup instructions.  
    -->  
    <serviceCredentials>  
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->  
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >  
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->  
      <knownCertificates>  
       <add storeLocation="LocalMachine"   
            storeName="TrustedPeople"   
            x509FindType="FindBySubjectName"   
            findValue="Alice"/>  
      </knownCertificates>  
     </issuedTokenAuthentication>  
     <serviceCertificate storeLocation="LocalMachine"  
                         storeName="My"  
                         x509FindType="FindBySubjectName"  
                         findValue="localhost"  />  
    </serviceCredentials>  
   </behavior>  
  </serviceBehaviors>  
 </behaviors>  
  
</system.serviceModel>  
```  
  
 Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenu SAML i ich integracji z programem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: Struktura zabezpieczeń:  
  
1.  Pisanie niestandardowych dostawcy tokenu SAML.  
  
     Przykład implementuje niestandardowego dostawcę tokenów SAML, który zwraca token zabezpieczający oparte na potwierdzenia języka SAML, dostarczonego w czasie tworzenia.  
  
     Aby wykonać to zadanie, niestandardowego dostawcy tokenu jest pochodną <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody. Ta metoda tworzy i zwraca nowy `SecurityToken`.  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
     // Create a SamlSecurityToken from the provided assertion  
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);  
  
     // Create a SecurityTokenSerializer that will be used to   
     // serialize the SamlSecurityToken  
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();  
     // Create a memory stream to write the serialized token into  
     // Use an initial size of 64Kb  
     MemoryStream s = new MemoryStream(UInt16.MaxValue);  
  
     // Create an XmlWriter over the stream  
     XmlWriter xw = XmlWriter.Create(s);  
  
     // Write the SamlSecurityToken into the stream  
     ser.WriteToken(xw, samlToken);  
  
     // Seek back to the beginning of the stream  
     s.Seek(0, SeekOrigin.Begin);  
  
     // Load the serialized token into a DOM  
     XmlDocument dom = new XmlDocument();  
     dom.Load(s);  
  
     // Create a KeyIdentifierClause for the SamlSecurityToken  
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();  
  
    // Return a GenericXmlToken from the XML for the   
    // SamlSecurityToken, the proof token, the valid from and valid  
    // until times from the assertion and the key identifier clause  
    // created above  
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);  
    }  
    ```  
  
2.  Zapis Menedżer tokenów zabezpieczających niestandardowych.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Klasa jest używana do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody. Menedżer tokenów zabezpieczających jest również używane do utworzenia wystawcy uwierzytelnienia tokenu i Serializator tokenu, ale te nie są objęte w tym przykładzie. W tej przykładowej zabezpieczeń niestandardowych dziedziczy Menedżer tokenów <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądanej metody do zwracania niestandardowego dostawcy tokenu SAML podczas przekazany wymagania tokenu wskazują, że tokenu SAML. Jeśli klasa poświadczeń klienta nie (zobacz krok 3) określił potwierdzenia, Menedżer tokenów zabezpieczających tworzy odpowiednie wystąpienie.  
  
    ```  
    public class SamlSecurityTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
     SamlClientCredentials samlClientCredentials;  
  
     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)  
      : base(samlClientCredentials)  
     {  
      // Store the creating client credentials  
      this.samlClientCredentials = samlClientCredentials;  
     }  
  
     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
     {  
      // If token requirement matches SAML token return the   
      // custom SAML token provider  
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||  
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")  
      {  
       // Retrieve the SAML assertion and proof token from the   
       // client credentials  
       SamlAssertion assertion = this.samlClientCredentials.Assertion;  
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;  
  
       // If either the assertion of proof token is null...  
       if (assertion == null || prooftoken == null)  
       {  
        // ...get the SecurityBindingElement and then the   
        // specified algorithm suite  
        SecurityBindingElement sbe = null;  
        SecurityAlgorithmSuite sas = null;  
  
        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))  
        {  
         sas = sbe.DefaultAlgorithmSuite;  
        }  
  
        // If the token requirement is for a SymmetricKey based token..  
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)  
        {  
         // Create a symmetric proof token  
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );  
         // and a corresponding assertion based on the claims specified in the client credentials  
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);  
        }  
        // otherwise...  
        else  
        {  
         // Create an asymmetric proof token  
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();  
         // and a corresponding assertion based on the claims   
         // specified in the client credentials  
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );  
        }  
       }  
  
       // Create a SamlSecurityTokenProvider based on the assertion and proof token  
       return new SamlSecurityTokenProvider(assertion, prooftoken);  
      }  
      // otherwise use base implementation  
      else  
      {  
       return base.CreateSecurityTokenProvider(tokenRequirement);  
      }  
    }  
    ```  
  
3.  Wpisz poświadczenia niestandardowego klienta.  
  
     Klasa poświadczeń klienta jest używana do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i Serializator tokenu zabezpieczeń.  
  
    ```  
    public class SamlClientCredentials : ClientCredentials  
    {  
     ClaimSet claims;  
     SamlAssertion assertion;  
     SecurityToken proofToken;  
  
     public SamlClientCredentials() : base()  
     {  
      // Set SupportInteractive to false to suppress Cardspace UI  
      base.SupportInteractive = false;  
     }  
  
     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )  
     {  
      // Just do reference copy given sample nature  
      this.assertion = other.assertion;  
      this.claims = other.claims;  
      this.proofToken = other.proofToken;  
     }  
  
     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }  
  
     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }  
     public ClaimSet Claims { get { return claims; } set { claims = value; } }  
  
     protected override ClientCredentials CloneCore()  
     {  
      return new SamlClientCredentials(this);  
     }  
  
     public override SecurityTokenManager CreateSecurityTokenManager()  
     {  
      // return custom security token manager  
      return new SamlSecurityTokenManager(this);  
     }  
    }  
    ```  
  
4.  Skonfigurować klienta do używania poświadczeń klienta.  
  
     Próbka usuwa domyślną klasę poświadczeń klienta i udostępnia nową klasę poświadczeń klienta, klient może używać poświadczeń klienta.  
  
    ```  
    // Create new credentials class  
    SamlClientCredentials samlCC = new SamlClientCredentials();  
  
    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case  
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");  
  
    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case  
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");  
  
    // Create some claims to put in the SAML assertion  
    IList<Claim> claims = new List<Claim>();  
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));  
    ClaimSet claimset = new DefaultClaimSet(claims);  
    samlCC.Claims = claimset;  
  
    // set new credentials  
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);  
    ```  
  
 W usłudze oświadczeń skojarzone z funkcją wywołującą są wyświetlane. Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiedni certyfikat do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.  
  
-   Tworzenie certyfikatu serwera:  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. `%SERVER_NAME%` Zmiennej określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Wartość domyślna w tym pliku wsadowego to localhost.  
  
     Certyfikat jest przechowywany w magazynie LocalMachine lokalizacji w mojej (osobiste).  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:  
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Tworzenie wystawcy certyfikatu.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzyć wystawcy certyfikatu do użycia. `%USER_NAME%` Zmiennej Nazwa wystawcy. Zmień tę wartość, aby określić nazwę wystawcy. Wartością domyślną w tym pliku wsadowego jest Alicji.  
  
     Certyfikat jest przechowywany w magazynie, w My znajdujące się w lokalizacji magazynie CurrentUser.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie wystawcy certyfikatu do magazynu zaufanych certyfikatów serwera.  
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów na serwerze przy użyciu certyfikatu wystawcy nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom z folderu instalacji próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia uruchomione z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
2.  Uruchom Service.exe z service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi dla usługi danych binarnych.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera. Plik Service.exe.config trzeba zaktualizować do uwzględnienia tej nowej nazwy certyfikatu. Można utworzyć certyfikatu serwera, modyfikując plik wsadowy pliku Setup.bat. Należy pamiętać, że plik pliku setup.bat należy uruchomić w oknie wiersza polecenia programu Visual Studio z uprawnieniami administratora. Należy ustawić `%SERVER_NAME%` zmienną do hosta w pełni kwalifikowaną nazwę komputera, na którym jest używany do obsługi usługi.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta. Ten krok nie jest konieczne, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.  
  
5.  W pliku Service.exe.config na komputerze usługi Zmień wartość adres podstawowy, aby określić nazwę komputera w pełni kwalifikowaną zamiast localhost.  
  
6.  Na komputerze, usługi uruchom Service.exe z wiersza polecenia.  
  
7.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.  
  
9. Na komputerze klienckim, otwórz `Client.exe` z poziomu okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
## <a name="see-also"></a>Zobacz też
