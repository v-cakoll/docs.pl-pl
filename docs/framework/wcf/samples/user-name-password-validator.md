---
title: Moduł weryfikacji nazwy użytkownika i hasła
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 553ccd69a02e057c5131128378611a19502e713d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424160"
---
# <a name="user-name-password-validator"></a>Moduł weryfikacji nazwy użytkownika i hasła
Ten przykład pokazuje, jak wdrożyć niestandardowy moduł sprawdzania poprawności UserNamePassword. Jest to przydatne w przypadkach, gdy żaden z wbudowanych trybów weryfikacji UserNamePassword nie jest odpowiedni dla wymagań aplikacji. na przykład, gdy pary username i Password są przechowywane w niektórych magazynach zewnętrznych, takich jak baza danych. Ten przykład pokazuje usługę, która ma niestandardowy moduł sprawdzania poprawności, który sprawdza dwie konkretne pary nazw użytkownika/hasła. Klient używa pary nazwa użytkownika/hasło do uwierzytelniania w usłudze.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Ponieważ każda osoba może utworzyć poświadczenia nazwy użytkownika, która używa par username/Password, które akceptuje niestandardowy moduł walidacji, usługa jest mniej bezpieczna niż domyślne zachowanie udostępniane przez standardowy moduł UserNamePassword. Standardowy moduł sprawdzania poprawności UserNamePassword próbuje zmapować podanej pary nazwa użytkownika/hasło na konto systemu Windows i niepowodzenie uwierzytelniania w przypadku niepowodzenia tego mapowania. Niestandardowego modułu sprawdzania UserNamePassword w tym przykładzie nie można używać w kodzie produkcyjnym, tylko do celów informacyjnych.

 W podsumowaniu ten przykład pokazuje, jak:

- Klienta można uwierzytelnić przy użyciu tokenu nazwy użytkownika.

- Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego UserNamePasswordValidator i sposób propagowania błędów niestandardowych z logiki weryfikacji nazwy użytkownika i hasła do klienta.

- Serwer jest uwierzytelniany przy użyciu certyfikatu X. 509 serwera.

 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji, App. config. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding`, które domyślnie używa uwierzytelniania WS-Security i username. Zachowanie usługi określa tryb `Custom` na potrzeby sprawdzania poprawności par nazwy użytkownika/hasła klienta wraz z typem klasy modułu walidacji. Zachowanie określa również certyfikat serwera przy użyciu elementu `serviceCertificate`. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jak `findValue` w [\<serviceCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Powiązanie klienta jest skonfigurowane z odpowiednim trybem i komunikatem `clientCredentialType`.

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
```

 Implementacja klienta prosi użytkownika o podanie nazwy użytkownika i hasła.

```csharp
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
string username = Console.ReadLine();
Console.WriteLine("   Enter password:");
string password = "";
ConsoleKeyInfo info = Console.ReadKey(true);
while (info.Key != ConsoleKey.Enter)
{
    if (info.Key != ConsoleKey.Backspace)
    {
        if (info.KeyChar != '\0')
        {
            password += info.KeyChar;
        }
        info = Console.ReadKey(true);
    }
    else if (info.Key == ConsoleKey.Backspace)
    {
        if (password != "")
        {
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 Ten przykład używa niestandardowego UserNamePasswordValidator do sprawdzania poprawności par nazw i haseł. Przykład implementuje `CustomUserNamePasswordValidator`, pochodzące z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Aby uzyskać więcej informacji, zobacz dokumentację dotyczącą <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Ten konkretny niestandardowy przykład modułu sprawdzania poprawności implementuje metodę `Validate`, aby akceptować dwie konkretne pary nazw użytkownika/hasła, jak pokazano w poniższym kodzie.

```csharp
public class CustomUserNameValidator : UserNamePasswordValidator
{
 // This method validates users. It allows in two users,
 // test1 and test2 with passwords 1tset and 2tset respectively.
 // This code is for illustration purposes only and
 // MUST NOT be used in a production environment because it
 // is NOT secure.
 public override void Validate(string userName, string password)
 {
  if (null == userName || null == password)
  {
   throw new ArgumentNullException();
  }

  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
  {
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 Po wdrożeniu modułu sprawdzania poprawności w kodzie usługi Host usługi musi zostać poinformowany o wystąpieniu modułu sprawdzania poprawności, które ma być używane. Jest to realizowane przy użyciu następującego kodu.

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Można też wykonać tę czynność w konfiguracji w następujący sposób.

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient powinien pomyślnie wywołać wszystkie metody. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

## <a name="setup-batch-file"></a>Plik wsadowy konfiguracji
 Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych maszynach lub działać w niezależnym przypadku.

 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.

- Tworzenie certyfikatu serwera:

     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia. Zmienna% nazwa_serwera% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartość domyślna to localhost.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta:

     Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze

1. Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.  
  
2. Uruchom usługę Service. exe z service\bin.  
  
3. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na wielu maszynach  
  
1. Utwórz katalog na komputerze usługi dla plików binarnych usługi.  
  
2. Skopiuj program Service Files do katalogu usługi na komputerze usługi. Skopiuj także pliki Setup. bat i Oczyść. bat do maszyny usługi.  
  
3. Potrzebny jest certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera. Plik konfiguracji dla serwera musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu.  
  
4. Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta. Należy to zrobić tylko wtedy, gdy certyfikat serwera nie zostanie wystawiony przez zaufanego wystawcy.  
  
5. W pliku App. config na komputerze usługi Zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego.  
  
6. Na komputerze usługi Uruchom program Service. exe w oknie wiersza polecenia.  
  
7. Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.  
  
9. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
1. Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu. Spowoduje to usunięcie certyfikatu serwera z magazynu certyfikatów.  
