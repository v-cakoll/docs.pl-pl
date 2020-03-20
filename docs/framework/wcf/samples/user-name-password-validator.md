---
title: Moduł weryfikacji nazwy użytkownika i hasła
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 202c7bfc7f60afbad8220950e46c08c0a71eb001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183250"
---
# <a name="user-name-password-validator"></a>Moduł weryfikacji nazwy użytkownika i hasła
W tym przykładzie pokazano, jak zaimplementować niestandardowy UserNamePassword Validator. Jest to przydatne w przypadkach, gdy żaden z wbudowanych trybów sprawdzania poprawności UserNamePassword nie jest odpowiedni dla wymagań aplikacji; na przykład, gdy pary nazwy użytkownika/hasła są przechowywane w niektórych magazynach zewnętrznych, takich jak baza danych. W tym przykładzie przedstawiono usługę, która ma niestandardowy walidator, który sprawdza dwie pary nazwy użytkownika/hasła. Klient używa takiej pary nazwy użytkownika/hasła do uwierzytelniania w usłudze.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Ponieważ każdy może skonstruować poświadczenia nazwy użytkownika, który używa pary nazwa użytkownika/hasło, które akceptuje niestandardowy walidator, usługa jest mniej bezpieczne niż domyślne zachowanie dostarczone przez standardowy UserNamePassword Walidator. Standardowy wznaczacz UserNamePassword próbuje zamapować podaną parę nazwa_użytkownika/hasło na konto systemu Windows i nie powiedzie się uwierzytelnienie, jeśli to mapowanie nie powiedzie się. Niestandardowy UserNamePassword Validator w tym przykładzie NIE MOGĄ być używane w kodzie produkcyjnym, jest tylko do celów ilustracyjnych.

 Podsumowując ten przykład pokazuje, jak:

- Klient może być uwierzytelniony przy użyciu tokenu nazwy użytkownika.

- Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego certyfikatu UserNamePasswordValidator oraz sposobu propagowania błędów niestandardowych z logiki sprawdzania poprawności nazwy użytkownika i hasła do klienta.

- Serwer jest uwierzytelniony przy użyciu certyfikatu X.509 serwera.

 Usługa udostępnia jeden punkt końcowy do komunikowania się z usługą, zdefiniowane przy użyciu pliku konfiguracji, App.config. Punkt końcowy składa się z adresu, powiązania i umowy. Powiązanie jest skonfigurowane `wsHttpBinding` ze standardem, który domyślnie używa WS-Security i uwierzytelniania nazwy użytkownika. Zachowanie usługi określa `Custom` tryb sprawdzania poprawności pary nazwy użytkownika/hasła klienta wraz z typem klasy walidatora. Zachowanie określa również certyfikat serwera `serviceCertificate` przy użyciu elementu. Certyfikat serwera musi zawierać taką samą `SubjectName` `findValue` wartość jak w [ \<>certyfikatu serviceCertificate ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, bezwzględny adres dla punktu końcowego usługi, powiązania i umowy. Powiązanie klienta jest skonfigurowane z `clientCredentialType`odpowiednim trybem i komunikatem .

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

 Implementacja klienta monituje użytkownika o wprowadzenie nazwy użytkownika i hasła.

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

 W tym przykładzie użyto niestandardowego userNamePasswordValidator do sprawdzania poprawności par nazwy użytkownika/hasła. Przykład implementuje, `CustomUserNamePasswordValidator`pochodzące <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>z . Aby uzyskać <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> więcej informacji, zapoznaj się z dokumentacją. Ten przykład niestandardowego walidatora implementuje `Validate` metodę akceptowania dwóch par nazwy użytkownika/hasła, jak pokazano w poniższym kodzie.

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

 Po zaimplementowaniu walidatora w kodzie usługi host usługi musi zostać poinformowany o wystąpieniu walidatora do użycia. Odbywa się to przy użyciu następującego kodu.

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Możesz też zrobić to samo w konfiguracji w następujący sposób.

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

 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient powinien pomyślnie wywołać wszystkie metody. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

## <a name="setup-batch-file"></a>Plik wsadowy instalatora
 Plik wsadowy Setup.bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie, która wymaga zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy musi być zmodyfikowany do pracy na różnych komputerach lub do pracy w przypadku nie-hosted.

 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować w celu uruchomienia w odpowiedniej konfiguracji.

- Tworzenie certyfikatu serwera:

     Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany. Zmienna %SERVER_NAME% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartością domyślną jest localhost.

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

     Następujące wiersze w pliku wsadowym Setup.bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i utworzyć próbkę

1. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Aby uruchomić próbkę w konfiguracji pojedynczej lub międzyprzerobanych, należy użyć następujących instrukcji.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić próbkę na tym samym komputerze

1. Uruchom plik Setup.bat z przykładowego folderu instalacji w wierszu polecenia programu Visual Studio 2012. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.

    > [!NOTE]
    > Plik wsadowy setup.bat jest przeznaczony do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zestaw zmiennych środowiskowych PATH w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup.bat.  
  
2. Uruchom program Service.exe z pliku service\bin.  
  
3. Uruchom program Client.exe z pliku \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Utwórz katalog na komputerze serwisowym dla plików binarnych usług.  
  
2. Skopiuj plik programu serwisowego katalogu usług na komputerze serwisowym. Skopiuj również pliki Setup.bat i Cleanup.bat do urządzenia serwisowego.  
  
3. Potrzebny jest certyfikat serwera o nazwie podmiotu zawierający w pełni kwalifikowaną nazwę domeny komputera. Plik konfiguracyjny serwera musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu.  
  
4. Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta. Należy to zrobić tylko wtedy, gdy certyfikat serwera nie jest wystawiony przez zaufanego wystawcę.  
  
5. W pliku App.config na komputerze serwisowym zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast localhost.  
  
6. Na komputerze serwisowym uruchom program Service.exe z okna wiersza polecenia.  
  
7. Skopiuj pliki programu klienckiego z folderu \client\bin\ w folderze specyficznym dla języka do komputera klienckiego.  
  
8. W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim uruchom program Client.exe z okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
1. Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki. Spowoduje to usunięcie certyfikatu serwera z magazynu certyfikatów.  
