---
title: Dostawca tokenów SAML
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 509469404e2c3866c26b5e1817a819519203c175
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747850"
---
# <a name="saml-token-provider"></a>Dostawca tokenów SAML
Ten przykład demonstruje sposób implementacji niestandardowego klienta Dostawca tokenów SAML. Dostawca tokenu w Windows Communication Foundation (WCF) jest używany dla podanie poświadczeń w celu infrastruktura zabezpieczeń. Dostawcy tokenu, który sprawdza ogólnie rzecz biorąc, element docelowy i problemy odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć wiadomości. Usługi WCF jest dostarczany z domyślny dostawca tokenu Menedżera poświadczeń. Usługi WCF jest również dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu. Niestandardowego dostawcy tokenów są przydatne w następujących przypadkach:  
  
-   Jeśli masz Magazyn poświadczeń, który te dostawcy tokenów nie może działać z.  
  
-   Jeśli chcesz udostępnić własny niestandardowy mechanizm przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje, na kiedy struktura klienta WCF przy użyciu poświadczeń.  
  
-   Jeśli tworzysz niestandardowy token.  
  
 Niniejszy przykład pokazuje sposób tworzenia niestandardowego dostawcę tokenów, który umożliwia tokenu SAML uzyskany z poza szablonem klienta WCF, który ma być używany.  
  
 Aby podsumować, w przykładzie pokazano poniżej:  
  
-   Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.  
  
-   Jak tokenu SAML mogą być przekazywane poświadczenia niestandardowego klienta.  
  
-   Jak struktura klienta programu WCF zapewnia SAML token.  
  
-   Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 serwera.  
  
 Usługa udostępnia dwa punkty końcowe dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego `wsFederationHttpBinding`, która używa zabezpieczenia komunikatów. Jeden punkt końcowy oczekuje klienta do uwierzytelniania za pomocą tokenu SAML, które używa klucza symetrycznego dowód, podczas gdy druga oczekuje klienta do uwierzytelniania przy użyciu tokenu SAML, która używa klucza asymetrycznego dowód. Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie. `serviceCredentials` Zachowanie umożliwia skonfigurowanie certyfikatu usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi, a także zapewnienia ochrony wiadomości. Następująca konfiguracja odwołuje się do certyfikatu "localhost" zainstalowany podczas instalacji przykładowej zgodnie z opisem w instrukcje instalacji, na końcu tego tematu. `serviceCredentials` Zachowanie umożliwia również konfigurowanie certyfikatów, które są zaufane, aby zarejestrować tokeny SAML. Następująca konfiguracja odwołuje się do certyfikatu "Alicja" instalowane w ramach przykładu.  
  
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
  
 Poniższe kroki pokazują jak utworzyć niestandardowy Dostawca tokenów SAML i zintegrować ją z usługą WCF: struktury zabezpieczeń:  
  
1.  Napisać niestandardowy Dostawca tokenów SAML.  
  
     Przykład implementuje niestandardowy Dostawca tokenów SAML, która zwraca token zabezpieczający, w oparciu o potwierdzenie SAML, który znajduje się w czasie tworzenia.  
  
     Aby wykonać to zadanie, niestandardowego dostawcy tokenów jest tworzony na podstawie <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody. Ta metoda tworzy i zwraca nowy `SecurityToken`.  
  
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
  
2.  Napisz Menedżer tokenów zabezpieczeń niestandardowych.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Klasa jest używana do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla konkretnego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody. Menedżer tokenów zabezpieczeń jest również używany do tworzenia wystawcy uwierzytelnienia tokenu i Serializator tokenów, ale te nie są objęte tego przykładu. W tym przykładowe niestandardowe zabezpieczeń, Menedżer tokenów dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądana jest metoda do zwrócenia niestandardowego dostawcy tokenów SAML przy przekazany wymagania tokenu wskazują, że SAML token. Jeśli klasa poświadczeń klienta nie (zobacz krok 3) określił potwierdzenie, Menedżer tokenów zabezpieczeń tworzy odpowiednie wystąpienie.  
  
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
  
     Klasa poświadczeń klienta jest używany do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy zabezpieczeń Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatora.  
  
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
  
4.  Konfigurowanie klienta do używania poświadczeń klienta.  
  
     Przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta, dzięki czemu klient może używać poświadczeń klienta.  
  
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
  
 W usłudze są wyświetlane oświadczenia skojarzone z funkcją wywołującą. Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera z odpowiedni certyfikat, aby uruchomić samodzielnie hostowanej aplikacji, która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.  
  
 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.  
  
-   Tworzenie certyfikatu serwera:  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%` Zmienna Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Wartość domyślna, w tym pliku wsadowego to localhost.  
  
     Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu LocalMachine.  
  
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
  
     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Tworzenie certyfikatu wystawcy.  
  
     Następujące wiersze z pliku wsadowego Setup.bat Utwórz certyfikat wystawca ma być używany. `%USER_NAME%` Zmiennej określa nazwę wystawcy. Zmień tę wartość, aby określić nazwę wystawcy. Wartość domyślna, w tym pliku wsadowego to Alicji.  
  
     Certyfikat jest przechowywany w magazynie użytkownika znajdujące się w lokalizacji magazynu CurrentUser.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu wystawcy do magazynu zaufanych certyfikatów serwera.  
  
     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów serwera za pomocą certyfikatu wystawcy nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom Setup.bat z folderu instalacji przykładowej wewnątrz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wierszu polecenia Uruchom z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Ustawić zmiennej środowiskowej PATH, w ramach [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia wskazuje katalog, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest.  
  
2.  Uruchom Service.exe z service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi, aby pliki binarne usługi.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera o nazwie podmiotu, który zawiera w pełni kwalifikowana nazwa domeny komputera. Plik Service.exe.config należy zaktualizować w celu odzwierciedlenia tej nowej nazwy certyfikatu. Można utworzyć certyfikatu serwera, modyfikując plik wsadowy Setup.bat. Należy pamiętać, że plik Setup.bat jest musi zostać uruchomiony w oknie wiersza polecenia programu Visual Studio otwartych z uprawnieniami administratora. Należy ustawić `%SERVER_NAME%` zmiennej do w pełni kwalifikowany host nazwę komputera, na którym jest używana do obsługi usługi.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta. Ten krok nie jest konieczne, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.  
  
5.  W pliku Service.exe.config na komputerze usługi Zmień wartość z adresu podstawowego, aby określić nazwę komputera w pełni kwalifikowaną, zamiast nazwy localhost.  
  
6.  Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.  
  
7.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim, należy uruchomić `Client.exe` z okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
## <a name="see-also"></a>Zobacz też
