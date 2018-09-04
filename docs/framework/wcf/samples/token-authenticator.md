---
title: Wystawca uwierzytelnienia tokenów
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 5c103f5a5a4f95761a5c19e6a8d6159a7439d05a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523223"
---
# <a name="token-authenticator"></a>Wystawca uwierzytelnienia tokenów
Ten przykład demonstruje sposób implementacji niestandardowego wystawcy uwierzytelniania tokenu. Wystawcy uwierzytelnienia tokenu w Windows Communication Foundation (WCF) służy do sprawdzania poprawności tokenu użytego komunikatem, weryfikowanie, czy jest spójny i uwierzytelniania tożsamości skojarzonych z tokenem.  
  
 Niestandardowe uwierzytelnienia tokenu są przydatne w wielu przypadkach, takich jak:  
  
-   Jeśli chcesz przesłonić domyślny mechanizm uwierzytelniania, skojarzone z tokenem.  
  
-   Kiedy tworzysz niestandardowy token.  
  
 W tym przykładzie pokazano poniżej:  
  
-   Jak klienta można uwierzytelniać za pomocą pary nazwy użytkownika i hasła.  
  
-   Jak serwer może sprawdzić poprawności poświadczeń klienta przy użyciu niestandardowego wystawcy uwierzytelniania tokenu.  
  
-   Jak kod usługi WCF wiąże się przy użyciu niestandardowego wystawcy uwierzytelniania tokenu.  
  
-   W jaki sposób serwer może zostać uwierzytelniony przy użyciu certyfikatu X.509 serwera.  
  
 Niniejszy przykład pokazuje również, jak tożsamości elementu wywołującego jest dostępny z WCF po zakończeniu procesu niestandardowe uwierzytelnianie przy użyciu tokenów.  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding`, tryb zabezpieczeń, ustawiono na komunikat — domyślny tryb `wsHttpBinding`. W tym przykładzie ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika klienta. Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie. `securityCredentials` Zachowanie pozwala określić certyfikat usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi, a także zapewnienia ochrony wiadomości. Następująca konfiguracja odwołuje się do certyfikatu localhost, instalowana podczas instalacji przykładowej zgodnie z opisem w poniższych instrukcjach instalacji.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate.  
          A service certificate is used by a client to authenticate the service and provide message protection.  
          This configuration references the "localhost" certificate installed during the setup instructions.  
....        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia. Klient powiązanie skonfigurowano odpowiednie `Mode` i `clientCredentialType`.  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint name=""  
                address="http://localhost:8000/servicemodelsamples/service"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
```  
  
 Implementacja klienta ustawia nazwę użytkownika i hasło do użycia.  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a>Niestandardowego wystawcy uwierzytelniania tokenu  
 Poniższe kroki umożliwiają tworzenie niestandardowego wystawcy uwierzytelniania tokenu:  
  
1.  Napisać niestandardowego wystawcy uwierzytelniania tokenu.  
  
     Przykład implementuje niestandardowe wystawcy uwierzytelnienia tokenu, który sprawdza, czy nazwa użytkownika ma format prawidłowy adres e-mail. Pochodzi <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Najważniejszą metodą w tej klasie jest <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. W przypadku tej metody wystawcy uwierzytelnienia weryfikuje format nazwy użytkownika oraz że nazwa hosta nie jest z domeny nieautoryzowanych. Jeśli oba warunki są spełnione, a następnie zwraca kolekcję tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystąpień, które jest następnie używany w celu dostarczania oświadczeń, które reprezentują informacje przechowywane w tokenie nazwy użytkownika.  
  
    ```  
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)  
    {  
        if (!ValidateUserNameFormat(userName))  
            throw new SecurityTokenValidationException("Incorrect UserName format");  
  
        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));  
        List<IIdentity> identities = new List<IIdentity>(1);  
        identities.Add(new GenericIdentity(userName));  
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));  
        return policies.AsReadOnly();  
    }  
    ```  
  
2.  Podaj zasady autoryzacji, który jest zwracany przez niestandardowego wystawcy uwierzytelniania tokenu.  
  
     W tym przykładzie zawiera własną implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> o nazwie `UnconditionalPolicy` zwracającego zestawu oświadczeń i tożsamości, które zostały przekazane do niego w jego konstruktorze.  
  
    ```  
    class UnconditionalPolicy : IAuthorizationPolicy  
    {  
        String id = Guid.NewGuid().ToString();  
        ClaimSet issuer;  
        ClaimSet issuance;  
        DateTime expirationTime;  
        IList<IIdentity> identities;  
  
        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)  
        {  
            if (issuer == null)  
                throw new ArgumentNullException("issuer");  
            if (issuance == null)  
                throw new ArgumentNullException("issuance");  
  
            this.issuer = issuer;  
            this.issuance = issuance;  
            this.identities = identities;  
            this.expirationTime = expirationTime;  
        }  
  
        public string Id  
        {  
            get { return this.id; }  
        }  
  
        public ClaimSet Issuer  
        {  
            get { return this.issuer; }  
        }  
  
        public DateTime ExpirationTime  
        {  
            get { return this.expirationTime; }  
        }  
  
        public bool Evaluate(EvaluationContext evaluationContext, ref object state)  
        {  
            evaluationContext.AddToTarget(this, this.issuance);  
  
            if (this.identities != null)  
            {  
                object value;  
                IList<IIdentity> contextIdentities;  
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))  
                {  
                    contextIdentities = new List<IIdentity>(this.identities.Count);  
                    evaluationContext.Properties.Add("Identities", contextIdentities);  
                }  
                else  
                {  
                    contextIdentities = value as IList<IIdentity>;  
                }  
                foreach (IIdentity identity in this.identities)  
                {  
                    contextIdentities.Add(identity);  
                }  
            }  
  
            evaluationContext.RecordExpirationTime(this.expirationTime);  
            return true;  
        }  
    }  
    ```  
  
3.  Napisać niestandardowy token Menedżer zabezpieczeń.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> dla konkretnego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> obiekty, które są przekazywane do niego w `CreateSecurityTokenAuthenticator` metody. Menedżer tokenów zabezpieczeń umożliwia również tworzenie dostawcy tokenów i tokenów serializatory, ale te nie są objęte tego przykładu. W tym przykładzie Menedżer tokenów zabezpieczeń niestandardowe dziedziczy <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenAuthenticator` żądana jest metoda do zwrócenia wystawcy uwierzytelniania tokenu niestandardowej nazwy użytkownika, jeśli przekazany wymagania tokenu wskazać, że uwierzytelniania nazwy użytkownika.  
  
    ```  
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager  
    {  
        MyUserNameCredential myUserNameCredential;  
  
        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)  
            : base(myUserNameCredential)  
        {  
            this.myUserNameCredential = myUserNameCredential;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)  
            {  
                outOfBandTokenResolver = null;  
                return new MyTokenAuthenticator();  
            }  
            else  
            {  
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
            }  
        }  
    }  
    ```  
  
4.  Wpisz poświadczenia usługi niestandardowych.  
  
     Klasa poświadczenia usługi jest używana do reprezentowania poświadczenia, które są skonfigurowane dla usługi i tworzy zabezpieczeń Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatory.  
  
    ```  
    public class MyUserNameCredential : ServiceCredentials  
    {  
  
        public MyUserNameCredential()  
            : base()  
        {  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new MyUserNameCredential();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new MySecurityTokenManager(this);  
        }  
  
    }  
    ```  
  
5.  Skonfiguruj usługę pod kątem używania poświadczeń usługi niestandardowych.  
  
     Aby usługi w celu używania poświadczeń usługa niestandardowa możemy usunąć domyślną klasę poświadczeń usługi po przechwyceniu certyfikat usługi, która jest już wstępnie skonfigurowane w domyślnych poświadczeń usługi, a następnie skonfigurować nowe poświadczenie usługi wystąpienie do używania certyfikatów wstępnie skonfigurowane usługi i dodaj to nowe wystąpienie poświadczeń usługi do zachowania usługi.  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 Aby wyświetlić informacje dotyczące obiektu wywołującego, można użyć <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym kodzie. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera oświadczenia informacje dotyczące bieżącego obiektu wywołującego.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia samodzielnie hostowanej aplikacji, która wymaga serwera zabezpieczeń opartego na certyfikatach. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.  
  
 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%` Zmienna Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Domyślnie ten plik wsadowy jest localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.  
  
     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Instalacyjny plik wsadowy jest przeznaczony do uruchamiania z wierszem polecenia Windows SDK. Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia Windows SDK.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom Setup.bat z folderu instalacji przykładowej wewnątrz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia otwartych z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Ustawić zmiennej środowiskowej PATH, w ramach [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia wskazuje katalog, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest.  
  
2.  Uruchom service.exe z service\bin.  
  
3.  Uruchom client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi, aby pliki binarne usługi.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera o nazwie podmiotu, który zawiera w pełni kwalifikowana nazwa domeny komputera. Plik App.config usługi należy zaktualizować w celu odzwierciedlenia tej nowej nazwy certyfikatu. Możesz je utworzyć za pomocą Setup.bat, jeśli ustawisz `%SERVER_NAME%` zmiennych hosta w pełni kwalifikowaną nazwę komputera, na którym uruchomiona jest usługa. Należy pamiętać, że plik Setup.bat jest należy uruchomić z wiersza polecenia programu Visual Studio, otwartych z uprawnieniami administratora.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta. Nie trzeba to zrobić, z wyjątkiem sytuacji, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.  
  
5.  W pliku App.config na komputerze usługi Zmień wartość z adresu podstawowego, aby określić nazwę komputera w pełni kwalifikowaną, zamiast nazwy localhost.  
  
6.  Na komputerze usługi service.exe należy uruchomić z wiersza polecenia.  
  
7.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
## <a name="see-also"></a>Zobacz też
