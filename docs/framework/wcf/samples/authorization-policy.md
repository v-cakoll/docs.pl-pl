---
title: Zasady autoryzacji
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 9b73eea1f51454dd82ba577c4d4d5fd5a1c0efd4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990189"
---
# <a name="authorization-policy"></a>Zasady autoryzacji

Ten przykład pokazuje, jak zaimplementować niestandardowe zasady autoryzacji i skojarzonego z nim niestandardowego Menedżera autoryzacji usług. Jest to przydatne, gdy usługa przeprowadza kontrolę dostępu opartą na usługach i przed sprawdzenia dostępu, przyznaje wywołującemu pewne prawa. Ten przykład pokazuje proces dodawania oświadczeń oraz proces przeprowadzania sprawdzenia dostępu względem końcowego zestawu oświadczeń. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i szyfrowane. Domyślnie przy użyciu `wsHttpBinding` powiązania nazwa użytkownika i hasło podane przez klienta są używane do logowania do prawidłowego konta systemu Windows NT. Ten przykład pokazuje, jak używać niestandardowych <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> do uwierzytelniania klienta. Dodatkowo ten przykład pokazuje klienta uwierzytelniającego się do usługi przy użyciu certyfikatu X. 509. Ten przykład pokazuje implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i <xref:System.ServiceModel.ServiceAuthorizationManager>, która między nimi udziela dostępu do określonych metod usługi dla określonych użytkowników. Ten przykład jest oparty na [nazwie użytkownika zabezpieczeń wiadomości](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale pokazuje, jak przeprowadzić transformację roszczeń przed <xref:System.ServiceModel.ServiceAuthorizationManager> wywoływaniem.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

 Podsumowując, w tym przykładzie pokazano, jak:

- Klienta można uwierzytelnić przy użyciu nazwy użytkownika i hasła.

- Klienta można uwierzytelnić przy użyciu certyfikatu X. 509.

- Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego `UsernamePassword` modułu sprawdzania poprawności.

- Serwer jest uwierzytelniany przy użyciu certyfikatu X. 509 serwera.

- Serwer może służyć <xref:System.ServiceModel.ServiceAuthorizationManager> do kontrolowania dostępu do określonych metod w usłudze.

- Jak zaimplementować <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Usługa udostępnia dwa punkty końcowe do komunikacji z usługą, zdefiniowane przy użyciu pliku konfiguracji App. config. Każdy punkt końcowy składa się z adresu, powiązania i kontraktu. Jedno powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, które korzysta z uwierzytelniania WS-Security i nazwy użytkownika klienta. Inne powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, które korzysta z protokołu WS-Security i uwierzytelniania certyfikatu klienta. Zachowanie > określa, że poświadczenia użytkownika mają być używane do uwierzytelniania usługi. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Certyfikat serwera musi zawierać tę samą wartość `SubjectName` właściwości `findValue` , co atrybut w [ \<> serviceCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

Każda konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Powiązanie klienta jest skonfigurowane z odpowiednim trybem zabezpieczeń określonym w tym przypadku w [ \<> zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) i `clientCredentialType` zgodnie z opisem w [ \<> komunikatów](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

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

W przypadku punktu końcowego opartego na nazwie użytkownika implementacja klienta ustawia nazwę użytkownika i hasło, które mają być używane.

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

W przypadku punktu końcowego opartego na certyfikatach implementacja klienta ustawia używany certyfikat klienta.

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

Ten przykład używa niestandardowych <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> do sprawdzania poprawności nazw użytkowników i haseł. Przykład implementuje `MyCustomUserNamePasswordValidator`, pochodny od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Zapoznaj się z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> dokumentacją, aby uzyskać więcej informacji. W celu demonstrowania integracji z programem <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>ten niestandardowy przykład modułu sprawdzania poprawności <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> implementuje metodę, aby akceptować pary nazwa użytkownika/hasło, gdzie nazwa użytkownika jest zgodna z hasłem, jak pokazano w poniższym kodzie.

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

Po wdrożeniu modułu sprawdzania poprawności w kodzie usługi Host usługi musi zostać poinformowany o wystąpieniu modułu sprawdzania poprawności, które ma być używane. W tym celu należy użyć następującego kodu:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Można też wykonać te same czynności w konfiguracji:

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

Windows Communication Foundation (WCF) oferuje bogaty model oparty na oświadczeniach służący do przeprowadzania kontroli dostępu. <xref:System.ServiceModel.ServiceAuthorizationManager> Obiekt jest używany do sprawdzania dostępu i ustalania, czy oświadczenia skojarzone z klientem spełniają wymagania niezbędne do uzyskania dostępu do metody usługi.

W celach demonstracyjnych ten przykład pokazuje implementację <xref:System.ServiceModel.ServiceAuthorizationManager> , która <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> implementuje metodę, aby zezwolić użytkownikowi na dostęp do metod opartych na oświadczeniach typu `http://example.com/claims/allowedoperation` , którego wartość jest identyfikator URI akcji operacji, która jest mogą być wywoływane.

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

Po zaimplementowaniu niestandardowego <xref:System.ServiceModel.ServiceAuthorizationManager> hosta usługi należy poinformować o tym <xref:System.ServiceModel.ServiceAuthorizationManager> , aby można było go użyć. Jest to wykonywane, jak pokazano w poniższym kodzie.

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Podstawową <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metodą implementacji <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> jest metoda.

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

Poprzedni kod pokazuje, w <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> jaki sposób Metoda sprawdza, czy nie dodano żadnych nowych oświadczeń, które wpływają na przetwarzanie i dodaje określone oświadczenia. Oświadczenia, które są dozwolone, są uzyskiwane `GetAllowedOpList` z metody, która jest zaimplementowana w celu zwrócenia określonej listy operacji, które użytkownik może wykonywać. Zasady autoryzacji dodają oświadczenia w celu uzyskania dostępu do określonej operacji. Jest to później używane przez <xref:System.ServiceModel.ServiceAuthorizationManager> program do wykonywania decyzji o sprawdzaniu dostępu.

Po zaimplementowaniu niestandardowego <xref:System.IdentityModel.Policy.IAuthorizationPolicy> hosta usługi należy uzyskać informacje o zasadach autoryzacji do użycia.

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie wywołuje metody Add, Odejmij i Multiple i pobiera komunikat "odmowa dostępu" podczas próby wywołania metody dzielenia. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

## <a name="setup-batch-file"></a>Plik wsadowy konfiguracji

Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.

Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji:

- Tworzenie certyfikatu serwera.

    Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia. Zmienna% nazwa_serwera% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartość domyślna to localhost.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.

    Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Tworzenie certyfikatu klienta.

    Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat klienta, który ma być używany. Zmienna% nazwa_użytkownika% Określa nazwę serwera. Ta wartość jest ustawiona na "test1", `IAuthorizationPolicy` ponieważ jest to nazwa szukana. W przypadku zmiany wartości% nazwa_użytkownika% należy zmienić odpowiadającą jej wartość w `IAuthorizationPolicy.Evaluate` metodzie.

    Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu klienta w zaufanym magazynie certyfikatów na serwerze.

    Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat klienta do magazynu osób zaufanych. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert. exe nie są niejawnie zaufane przez system serwera. Jeśli masz już certyfikat, który został odblokowany w zaufanym certyfikacie głównym — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów serwera z certyfikatem klienta nie jest wymagany.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.

> [!NOTE]
> Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom *Setup. bat* z przykładowego folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersz polecenia dla deweloperów dla programu Visual Studio. Zmienna środowiskowa PATH ustawiona w wiersz polecenia dla deweloperów dla programu Visual Studio wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt *Setup. bat* .

1. Uruchom Service. exe z *service\bin*.

1. Uruchom plik Client. exe z *\client\bin*. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.

Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach

1. Utwórz katalog na komputerze usługi.

2. Skopiuj pliki programu usługi z *\service\bin* do katalogu na komputerze usługi. Skopiuj także pliki Setup. bat, Oczyść. bat, getcomputers. vbs i ImportClientCert. bat do komputera usługi.

3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.

4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.

5. Na serwerze programu uruchom `setup.bat service` program w wiersz polecenia dla deweloperów for Visual Studio otwarty z uprawnieniami administratora.

    `setup.bat` Uruchomienie`service` z argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie *Service. cer*.

6. Edytuj *plik Service. exe. config* , aby odzwierciedlić nową nazwę certyfikatu ( `findValue` w atrybucie w [ \<> serviceCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera. Zmień również **ComputerName** w \<> usługi/\<baseAddresses > z localhost na w pełni kwalifikowaną nazwę komputera usługi.

7. Skopiuj plik *. cer usługi* z katalogu usługi do katalogu klienta na komputerze klienckim.

8. Na kliencie Uruchom `setup.bat client` program w wiersz polecenia dla deweloperów dla programu Visual Studio, który został otwarty z uprawnieniami administratora.

    Uruchomienie `setup.bat` z argumentem tworzy certyfikat klienta o nazwie TEST1 i eksportuje certyfikat klienta do pliku o nazwie *Client. cer.* `client`

9. W pliku *Client. exe. config* na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Aby to zrobić, Zastąp wartość **localhost** nazwą FQDN serwera.

10. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.

11. Na kliencie Uruchom program *ImportServiceCert. bat* w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.

    Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu **CurrentUser-TrustedPeople** .

12. Na serwerze uruchom program *ImportClientCert. bat* w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.

    Spowoduje to zaimportowanie certyfikatu klienta z pliku. cer klienta do magazynu **LocalMachine-TrustedPeople** .

13. Na komputerze serwera Uruchom polecenie Service. exe w oknie wiersza polecenia.

14. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.

    Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Wyczyść po przykładzie

Aby wyczyścić po próbie, uruchom polecenie *Oczyść. bat* w folderze Samples po zakończeniu uruchamiania przykładu. Spowoduje to usunięcie certyfikatów serwera i klienta z magazynu certyfikatów.

> [!NOTE]
> Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów WCF, które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
