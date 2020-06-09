---
title: Dostawca tokenów
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: acdb820206dee83ff44152a5562642a5c685d648
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584080"
---
# <a name="token-provider"></a>Dostawca tokenów
Ten przykład pokazuje, jak zaimplementować niestandardowego dostawcę tokenów. Dostawca tokenu w Windows Communication Foundation (WCF) służy do dostarczania poświadczeń do infrastruktury zabezpieczeń. Dostawca tokenu ogólnie bada cel i wystawia odpowiednie poświadczenia, aby infrastruktura zabezpieczeń mogła zabezpieczyć komunikat. Usługa WCF jest dostarczana z domyślnym dostawcą tokenu Menedżera poświadczeń. Usługa WCF jest również dostarczana z dostawcą tokenu programu CardSpace. Dostawcy tokenów niestandardowych są przydatne w następujących przypadkach:

- Jeśli masz magazyn poświadczeń, którego nie mogą używać dostawcy tokenu.

- Jeśli chcesz zapewnić własny niestandardowy mechanizm przekształcania poświadczeń z punktu, gdy użytkownik poda szczegółowe informacje o tym, kiedy struktura klienta programu WCF używa tych poświadczeń.

- W przypadku kompilowania niestandardowego tokenu.

 Ten przykład pokazuje, jak utworzyć niestandardowego dostawcę tokenów, który przekształca dane wejściowe użytkownika w inny format.

 Podsumowując, ten przykład ilustruje następujące elementy:

- Jak klient może uwierzytelniać za pomocą pary username/Password.

- Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.

- Sposób, w jaki serwer może sprawdzać poprawność poświadczeń klienta przy użyciu hasła z niestandardowym <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , które sprawdza, czy nazwa użytkownika i hasło są zgodne.

- Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X. 509 serwera.

 Ten przykład pokazuje również, jak tożsamość wywołującego jest dostępna po procesie uwierzytelniania tokenu niestandardowego.

 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji App. config. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane przy użyciu standardu `wsHttpBinding` , który domyślnie używa zabezpieczeń komunikatów. Ten przykład ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika klienta. Usługa konfiguruje również certyfikat usługi przy użyciu zachowania ServiceCredentials. Zachowanie serviceCredentials służy do konfigurowania certyfikatu usługi. Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewniania ochrony komunikatów. Następująca konfiguracja odwołuje się do certyfikatu localhost zainstalowanego podczas konfiguracji przykładowej zgodnie z opisem w poniższych instrukcjach dotyczących instalacji.

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
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
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Powiązanie klienta jest skonfigurowane z odpowiednim `Mode` komunikatem i `clientCredentialType` .

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

 Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenów i zintegrować go z platformą zabezpieczeń WCF:

1. Napisz niestandardowego dostawcę tokenów.

     Przykład implementuje niestandardowego dostawcę tokenów, który uzyskuje nazwę użytkownika i hasło. Hasło musi być zgodne z tą nazwą użytkownika. Ten niestandardowy dostawca tokenów służy tylko do celów demonstracyjnych i nie jest zalecany w przypadku rzeczywistego wdrożenia.

     Aby wykonać to zadanie, dostawca niestandardowego tokenu dziedziczy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasę i zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metodę. Ta metoda tworzy i zwraca nowy `UserNameSecurityToken` .

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. Napisz niestandardowego menedżera tokenów zabezpieczających.

     Służy <xref:System.IdentityModel.Selectors.SecurityTokenManager> do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , które są przesyłane do niego w `CreateSecurityTokenProvider` metodzie. Menedżer tokenów zabezpieczających jest również używany do tworzenia wystawców tokenów i serializatorów tokenów, ale te nie są objęte tym przykładem. W tym przykładzie niestandardowy Menedżer tokenów zabezpieczających dziedziczy z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i przesłania `CreateSecurityTokenProvider` metodę w celu zwrócenia niestandardowego dostawcy tokenów username, gdy spełnione wymagania dotyczące tokenu wskazują, że zażądano dostawcy nazwy użytkownika.

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. Napisz niestandardowe poświadczenie klienta.

     Klasa poświadczeń klienta służy do reprezentowania poświadczeń skonfigurowanych dla serwera proxy klienta i tworzy Menedżera tokenów zabezpieczeń, który jest używany do uzyskiwania wystawców tokenów, dostawców tokenów i serializatorów tokenów.

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. Skonfiguruj klienta tak, aby korzystał z niestandardowego poświadczenia klienta.

     Aby klient korzystał z niestandardowego poświadczenia klienta, przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 Aby wyświetlić informacje o wywołującym w usłudze, użyj, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym przykładzie kodu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>Zawiera informacje o oświadczeniach dotyczących bieżącego obiektu wywołującego.

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

## <a name="setup-batch-file"></a>Plik wsadowy konfiguracji
 Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednim certyfikatem w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.

 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji:

- Tworzenie certyfikatu serwera.

     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia. `%SERVER_NAME%`Zmienna określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartość domyślna w tym pliku wsadowym to localhost.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta:

     Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> Plik wsadowy Setup. bat został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK. Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK.

#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 otwartym z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.  
  
2. Uruchom usługę Service. exe z service\bin.  
  
3. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. W wierszu polecenia wpisz nazwę użytkownika.  
  
5. W monicie o hasło Użyj tego samego ciągu, który został wpisanych dla monitu o podanie nazwy użytkownika.  
  
6. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Utwórz katalog na komputerze usługi dla plików binarnych usługi.  
  
2. Skopiuj pliki programu Service Files do katalogu usługi na komputerze usługi. Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.  
  
3. Musisz mieć certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera. Plik Service. exe. config musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu. Można utworzyć certyfikat serwera, modyfikując plik wsadowy Setup. bat. Należy pamiętać, że plik Setup. bat musi być uruchamiany z wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Należy ustawić `%SERVER_NAME%` zmienną na w pełni kwalifikowaną nazwę hosta komputera, który jest używany do hostowania usługi.  
  
4. Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta. Nie trzeba tego robić, gdy certyfikat serwera zostanie wystawiony przez zaufanego wystawcy klienta.  
  
5. W pliku Service. exe. config na komputerze usługi Zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego.  
  
6. Na komputerze usługi Uruchom program Service. exe z wiersza polecenia.  
  
7. Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.  
  
9. Na komputerze klienckim uruchom `Client.exe` polecenie w oknie wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
1. Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
