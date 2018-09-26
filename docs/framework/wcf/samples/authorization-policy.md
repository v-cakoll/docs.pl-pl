---
title: Zasady autoryzacji
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 78ca42abfd2df56edeeb273fcd8ba585aa16f635
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198322"
---
# <a name="authorization-policy"></a>Zasady autoryzacji

Ten przykład demonstruje sposób implementacji zasad autoryzacji oświadczenia niestandardowego i skojarzona usługa niestandardowego Menedżera autoryzacji. Jest to przydatne, kiedy usług ułatwia kontrole dostępu oparta na oświadczeniach, do operacji usługi i kontroli dostępu, udziela obiekt wywołujący pewne prawa. W tym przykładzie przedstawiono proces dodawania oświadczeń, a także proces ten kontrolę dostępu dla ukończonego zestaw oświadczeń. Wszystkie komunikaty aplikacji między klientem i serwerem są podpisane i szyfrowane. Domyślnie `wsHttpBinding` powiązania nazwy użytkownika i hasło podane przez klienta są używane do logowania się do prawidłowego konta Windows NT. W tym przykładzie pokazano, jak korzystanie z niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> do uwierzytelniania klienta. Ponadto ten przykład pokazuje klienta uwierzytelniania usługi przy użyciu certyfikatu X.509. Ten przykład pokazuje implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i <xref:System.ServiceModel.ServiceAuthorizationManager>, który między nimi udzielić dostępu do określonych metod usługi dla określonych użytkowników. Ten przykład jest oparty na [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale pokazuje, jak przeprowadzić przekształcania oświadczeń w programach starszych niż program <xref:System.ServiceModel.ServiceAuthorizationManager> wywoływana.

> [!NOTE]
> Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

 Podsumowując, ten przykład pokazuje, jak:

-   Klient może zostać uwierzytelniony przy użyciu nazwy — hasło użytkownika.

-   Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.

-   Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego `UsernamePassword` modułu sprawdzania poprawności.

-   Serwer jest uwierzytelniany przy użyciu certyfikatu X.509 serwera.

-   Serwer może używać <xref:System.ServiceModel.ServiceAuthorizationManager> kontrolować dostęp do pewnych metod w usłudze.

-   Jak zaimplementować <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Usługa udostępnia dwa punkty końcowe dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązanie i kontrakt. Jedno powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, który używa uwierzytelniania nazwy użytkownika protokołu WS-Security i klienta. Inne powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, który używa uwierzytelniania certyfikatu usługi WS-Security i klienta. [ \<Zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Określa, czy poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` właściwość jako `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
          <clientCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

Każdej konfiguracji punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia. Powiązanie skonfigurowaniu klienta w trybie zabezpieczeń odpowiednich podaną w tym przypadku w [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) i `clientCredentialType` określonej [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

Dla użytkowników na podstawie nazwy punktu końcowego implementacji klienta ustawia nazwę użytkownika i hasło do użycia.

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

Do endpoint opartego na certyfikatach implementacji klienta ustawia certyfikat klienta do użycia.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

W tym przykładzie użyto niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> do weryfikowania nazwy użytkownika i hasła. Implementuje próbki `MyCustomUserNamePasswordValidator`, pochodzącej z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Zobacz dokumentację na temat <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Aby uzyskać więcej informacji. Na potrzeby demonstrowania integracji z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, w tym przykładzie niestandardowego modułu weryfikacji implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę, aby zaakceptować pary nazwa/hasło użytkownika, jeśli nazwa użytkownika odpowiada hasło, jak pokazano w poniższym kodzie.

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
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
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

Po wdrożeniu modułu sprawdzania poprawności jest w kodzie usługi hosta usługi muszą zostać powiadomieni o wystąpieniu weryfikacji do użycia. Odbywa się przy użyciu następującego kodu:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Lub można zrobić to samo w konfiguracji:

```xml
<behavior ...>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) zapewnia rozbudowane modelu opartego na oświadczeniach do wykonywania kontroli dostępu. <xref:System.ServiceModel.ServiceAuthorizationManager> Obiekt jest używany do wykonywania kontroli dostępu i określić, czy oświadczenia skojarzone z klientami spełnia wymagania niezbędne do uzyskania dostępu do metody usługi.

Dla celów demonstracyjnych, w tym przykładzie pokazano implementację <xref:System.ServiceModel.ServiceAuthorizationManager> implementującej <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę, aby umożliwić użytkownikowi dostęp do metod na podstawie oświadczeń typu http://example.com/claims/allowedoperation którego wartością jest identyfikator URI akcji operacji, która jest może zostać wywołana.

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

Raz niestandardowe <xref:System.ServiceModel.ServiceAuthorizationManager> jest zaimplementowana, hosta usługi musi być poinformowany o <xref:System.ServiceModel.ServiceAuthorizationManager> do użycia. Odbywa się, jak pokazano w poniższym kodzie.

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Podstawowy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metody do zaimplementowania <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody.

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

W poprzednim kodzie sposób, w jaki <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda sprawdza, czy nie nowych oświadczeń został dodany, które wpływają na przetwarzanie i dodaje określonych oświadczeń. Oświadczenia, które są dozwolone są uzyskiwane z `GetAllowedOpList` metody, która jest zaimplementowana, aby zwrócić listę operacji, które użytkownik może wykonywać. Zasady autoryzacji dodaje oświadczenia do uzyskiwania dostępu do określonej operacji. Jest on używany później przez <xref:System.ServiceModel.ServiceAuthorizationManager> przeprowadzić decyzji dotyczących kontroli dostępu.

Gdy niestandardowe <xref:System.IdentityModel.Policy.IAuthorizationPolicy> jest implementowana, host usługi musi być poinformowany o zasady autoryzacji do użycia.

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie wywołuje dodawania, odejmowania i wiele metod i pobiera komunikat "Odmowa dostępu" podczas próby wywołania metody dzielenia. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy

Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia aplikacji własnego wymagającego zabezpieczenia oparte na certyfikatach serwera.

Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:

-   Tworzenie certyfikatu serwera.

     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. % Zmienna % nazwa_serwera Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Wartość domyślna to hosta lokalnego.

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

     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ certyfikaty, które są generowane przez Makecert.exe nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Tworzenie certyfikatu klienta.

     Następujące wiersze z pliku wsadowego Setup.bat utworzenia certyfikatu klienta, który ma być używany. % Zmienna % nazwa_użytkownika Określa nazwę serwera. Ta wartość jest równa "test1", ponieważ jest to nazwa `IAuthorizationPolicy` szuka. Jeśli zmienisz wartość % nazwa_użytkownika należy zmienić odpowiednie wartości w `IAuthorizationPolicy.Evaluate` metody.

     Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu CurrentUser.

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.

     Następujące wiersze w pliku wsadowym Setup.bat skopiuj certyfikat klienta do magazynu osób zaufanych. Ten krok jest wymagany, ponieważ certyfikaty, które są generowane przez Makecert.exe nie niejawnie cieszą się zaufaniem systemu serwera. Jeśli masz już certyfikat, który jest ścieżką w zaufany certyfikat główny — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów serwera za pomocą certyfikatu klienta nie jest wymagane.

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Do uruchomienia przykładu w konfiguracji o jednym lub wielu komputerze, użyj poniższych instrukcji.

> [!NOTE]
> Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Otwórz wiersz polecenia programisty dla programu Visual Studio z uprawnieniami administratora i uruchom *Setup.bat* z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dla deweloperów programu Visual Studio. Zmiennej środowiskowej PATH ustawiona w wierszu polecenia dla deweloperów dla programu Visual Studio wskazuje katalog, który zawiera wymagane przez pliki wykonywalne *Setup.bat* skryptu.

1. Uruchom Service.exe z *service\bin*.

1. Uruchom Client.exe z *\client\bin*. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.

  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach

1. Utwórz katalog na komputerze usługi.

2. Skopiuj pliki programu usługi z *\service\bin* do katalogu na komputerze usługi. Także skopiować pliki Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat, aby komputer z usługą.

3. Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.

4. Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.

5. Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.

   Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie *Service.cer*.

6. Edytuj *Service.exe.config* aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera. Również zmienić **computername** w \<usługi > /\<baseAddresses > element z hostem lokalnym do w pełni kwalifikowanej nazwy komputera usługi.

7. Kopiuj *Service.cer* plików z katalogu usługi katalogu klienta na komputerze klienckim.

8. Na komputerze klienckim, należy uruchomić `setup.bat client` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.

   Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie **test1** i eksportuje certyfikat klienta do pliku o nazwie *Client.cer*.

9. W *Client.exe.config* pliku na komputerze klienckim, zmień wartość adresu punktu końcowego, aby dopasować nowy adres usługi. To zrobić przez zastąpienie **localhost** z w pełni kwalifikowana nazwa domeny serwera.

10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.

11. Na komputerze klienckim, należy uruchomić *ImportServiceCert.bat* w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.

   Zaimportowany certyfikat usługi z pliku Service.cer do **CurrentUser - TrustedPeople** przechowywania.

12. Na serwerze, uruchom *ImportClientCert.bat* w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.

   Zaimportowany certyfikat klienta z pliku Client.cer do **LocalMachine - TrustedPeople** przechowywania.

13. Na komputerze serwera uruchomić Service.exe z okna wiersza polecenia.

14. Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia.

   Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="clean-up-after-the-sample"></a>Wyczyść zasoby po ukończeniu próbki

Aby wyczyścić zasoby po próbki, należy uruchomić *Cleanup.bat* w folderze samples, po zakończeniu działa aplikacja przykładowa. Spowoduje to usunięcie certyfikaty klienta i serwera z magazynu certyfikatów.

> [!NOTE]
> Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Jeśli uruchamiasz przykłady WCF, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople przechowywania. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.