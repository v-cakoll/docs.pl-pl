---
title: "Wystawca uwierzytelnienia tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 559ce043c50582f40e2d7828ad74f6d16e2b81f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="token-authenticator"></a>Wystawca uwierzytelnienia tokenów
W tym przykładzie pokazano, jak do zaimplementowania niestandardowego wystawcy uwierzytelnienia tokenu. Wystawcy uwierzytelnienia tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do sprawdzania poprawności tokenu używane z komunikatu, sprawdzania jest spójny, czy uwierzytelnianie tożsamość skojarzona z tokenem.  
  
 Niestandardowe wystawcy uwierzytelnienia tokenu są przydatne w wielu przypadkach, takich jak:  
  
-   Jeśli chcesz przesłonić domyślny mechanizm uwierzytelniania, skojarzone z tokenem.  
  
-   Gdy tworzysz niestandardowy token.  
  
 W tym przykładzie przedstawiono poniżej:  
  
-   Jak klient może uwierzytelnić przy użyciu pary nazwy użytkownika i hasła.  
  
-   Jak serwer można sprawdzić poprawności poświadczeń klienta przy użyciu niestandardowego wystawcy uwierzytelnienia tokenu.  
  
-   Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodu usługi wiąże się przy użyciu niestandardowego wystawcy uwierzytelnienia tokenu.  
  
-   W jaki sposób serwer mogą być uwierzytelniane za pomocą certyfikatu X.509 serwera.  
  
 W tym przykładzie pokazano, jak tożsamość obiektu wywołującego jest dostępny z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] po procesie uwierzytelniania tokenu niestandardowego.  
  
 Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z normą `wsHttpBinding`, tryb zabezpieczeń, ustawiono na wiadomości - domyślnego trybu `wsHttpBinding`. W tym przykładzie ustawia standardowego `wsHttpBinding` uwierzytelniania nazwa użytkownika klienta. Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie. `securityCredentials` Zachowanie pozwala określić certyfikat usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewnienia ochrony wiadomości. Następująca konfiguracja odwołuje się do certyfikatu localhost zainstalowane podczas instalacji próbki zgodnie z opisem w poniższych instrukcjach instalacji.  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu. Klient powiązanie jest skonfigurowany z użyciem odpowiednich `Mode` i `clientCredentialType`.  
  
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
  
## <a name="custom-token-authenticator"></a>Wystawcy uwierzytelnienia tokenu niestandardowego  
 Poniższe kroki umożliwiają utworzenie niestandardowego wystawcy uwierzytelnienia tokenu:  
  
1.  Pisanie niestandardowych wystawcy uwierzytelnienia tokenu.  
  
     Przykład implementuje niestandardowego wystawcy uwierzytelnienia tokenu sprawdzania, czy nazwa użytkownika ma format prawidłowy adres e-mail. Dziedziczy <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Najważniejsze metody tej klasy jest <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. W przypadku tej metody, wystawcą uwierzytelnienia weryfikuje format nazwy użytkownika oraz że nazwa hosta nie jest z domeny nieautoryzowany. Jeśli spełnione są oba warunki, a następnie zwraca kolekcję tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystąpień, które są następnie używane do zapewnienia oświadczenia, które reprezentują informacje przechowywane w tokenie nazwy użytkownika.  
  
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
  
2.  Podaj zwróconego przez wystawcę uwierzytelnienia tokenów niestandardowe zasady autoryzacji.  
  
     W tym przykładzie przedstawiono własną implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> o nazwie `UnconditionalPolicy` zwracającą zestaw oświadczeń i tożsamości, które zostały przekazane do niego w jego konstruktora.  
  
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
  
3.  Pisanie niestandardowych zabezpieczeń Menedżer tokenów.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> obiektów, które są przekazywane do niego w `CreateSecurityTokenAuthenticator` metody. Menedżer tokenów zabezpieczających umożliwia również tworzenie dostawcy tokenów i serializatorów tokenu, ale te nie są objęte w tym przykładzie. W tym przykładzie Menedżer tokenów zabezpieczających niestandardowych dziedziczy <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenAuthenticator` metody zwracane wystawcy uwierzytelnienia tokenu niestandardowej nazwy użytkownika w przypadku przekazany wymagania tokenu wskazywać tego uwierzytelniania nazwa użytkownika jest wymagane.  
  
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
  
4.  Wpisz poświadczenia usługi niestandardowej.  
  
     Klasa poświadczenia usługi jest używana do reprezentowania poświadczenia, które są skonfigurowane dla usługi i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i serializatorów tokenu zabezpieczeń.  
  
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
  
5.  Skonfiguruj usługę, aby użyć poświadczeń usługi niestandardowej.  
  
     Aby usługa ma używać poświadczeń usługi niestandardowej firma Microsoft usunąć domyślną klasę poświadczeń usługi po przechwyceniu certyfikat usługi, który jest już wstępnie skonfigurowane w domyślnych poświadczeń usługi, a następnie skonfiguruj nowe poświadczenie usługi wystąpienie, które korzystają z certyfikatów usługi wstępnie skonfigurowane i dodać tego nowego wystąpienia poświadczeń usługi do zachowania usługi.  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 Aby wyświetlić informacje o wywołującym, można użyć <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym kodzie. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera oświadczenia informacje o bieżącym wywołującego.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia aplikacji hostowania samoobsługowego, który wymaga serwera zabezpieczeń opartego na certyfikatach. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. `%SERVER_NAME%` Zmiennej określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Domyślnie ten plik wsadowy jest localhost.  
  
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
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Instalacyjny plik wsadowy jest przeznaczony do uruchamiania z wiersza polecenia systemu Windows SDK. Wymaga ona, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia systemu Windows SDK.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom z folderu instalacji próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
2.  Uruchom service.exe z service\bin.  
  
3.  Uruchom client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi dla usługi danych binarnych.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera. Usługa pliku App.config trzeba zaktualizować do uwzględnienia tej nowej nazwy certyfikatu. Można go utworzyć przy użyciu pliku Setup.bat, jeśli ustawisz `%SERVER_NAME%` zmiennych hosta w pełni kwalifikowaną nazwę komputera, na którym uruchomiona jest usługa. Należy pamiętać, że plik pliku setup.bat należy uruchomić z wiersza polecenia programu Visual Studio została otwarta z uprawnieniami administratora.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta. Nie trzeba w tym celu z wyjątkiem po wystawieniu certyfikatu serwera przez klienta zaufanego wystawcy.  
  
5.  W pliku App.config na komputerze usługi Zmień wartość adres podstawowy, aby określić nazwę komputera w pełni kwalifikowaną zamiast localhost.  
  
6.  Na komputerze, usługi uruchom service.exe z wiersza polecenia.  
  
7.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.  
  
9. Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.  
  
10. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
## <a name="see-also"></a>Zobacz też
