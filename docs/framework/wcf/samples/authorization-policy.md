---
title: Zasady autoryzacji
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463946"
---
# <a name="authorization-policy"></a>Zasady autoryzacji

W tym przykładzie pokazano, jak zaimplementować niestandardowe zasady autoryzacji oświadczeń i skojarzonego menedżera autoryzacji usługi niestandardowej. Jest to przydatne, gdy usługa sprawia, że oparte na oświadczenia kontroli dostępu do operacji usługi i przed kontroli dostępu, przyznaje wywołującemu pewne prawa. W tym przykładzie przedstawiono zarówno proces dodawania oświadczeń, jak i proces sprawdzania dostępu względem sfinalizowanego zestawu oświadczeń. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane. Domyślnie za `wsHttpBinding` pomocą powiązania nazwa użytkownika i hasło dostarczone przez klienta są używane do logowania do prawidłowego konta systemu Windows NT. W tym przykładzie pokazano, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> jak korzystać z niestandardowego do uwierzytelniania klienta. Ponadto w tym przykładzie pokazano klienta uwierzytelniającego się w usłudze przy użyciu certyfikatu X.509. W tym przykładzie <xref:System.IdentityModel.Policy.IAuthorizationPolicy> <xref:System.ServiceModel.ServiceAuthorizationManager>przedstawiono implementację i , które między nimi udzielają dostępu do określonych metod usługi dla określonych użytkowników. Ten przykład jest oparty na [nazwę użytkownika zabezpieczeń wiadomości,](../../../../docs/framework/wcf/samples/message-security-user-name.md)ale pokazuje, <xref:System.ServiceModel.ServiceAuthorizationManager> jak wykonać transformację oświadczenia przed wywoływane.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

 Podsumowując, w tym przykładzie pokazano, jak:

- Klient może być uwierzytelniony przy użyciu nazwy użytkownika-hasła.

- Klient może być uwierzytelniony przy użyciu certyfikatu X.509.

- Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego `UsernamePassword` walidatora.

- Serwer jest uwierzytelniony przy użyciu certyfikatu X.509 serwera.

- Serwer może <xref:System.ServiceModel.ServiceAuthorizationManager> służyć do kontrolowania dostępu do niektórych metod w usłudze.

- Jak wdrożyć <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Usługa udostępnia dwa punkty końcowe do komunikowania się z usługą, zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązania i umowy. Jedno powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, które używa uwierzytelniania w uchronienia klienta i uwierzytelniania nazwy użytkownika klienta. Inne powiązanie jest skonfigurowane `wsHttpBinding` przy użyciu standardowego powiązania, które używa usługi WS-Security i uwierzytelniania certyfikatu klienta. [ \<Zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) określa, że poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką `SubjectName` samą `findValue` wartość właściwości jak atrybut w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

Każda konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, bezwzględny adres dla punktu końcowego usługi, powiązania i umowy. Powiązanie klienta jest skonfigurowane w odpowiednim trybie zabezpieczeń określonym w `clientCredentialType` tym przypadku w>[ \<zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) i jak określono w [ \<komunikacie>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

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

W przypadku punktu końcowego opartego na nazwie użytkownika implementacja klienta ustawia nazwę użytkownika i hasło do użycia.

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

W przypadku punktu końcowego opartego na certyfikatach implementacja klienta ustawia certyfikat klienta do użycia.

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

W tym przykładzie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> użyto niestandardowego sprawdzania poprawności nazw użytkowników i haseł. Przykład implementuje, `MyCustomUserNamePasswordValidator`pochodzące <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>z . Więcej informacji <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> można znaleźć w dokumentacji. W celu wykazania integracji z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, ten przykład niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> walidatora implementuje metodę akceptowania par nazwy użytkownika/hasła, w których nazwa użytkownika jest zgodna z hasłem, jak pokazano w poniższym kodzie.

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

Po zaimplementowaniu walidatora w kodzie usługi host usługi musi zostać poinformowany o wystąpieniu walidatora do użycia. Odbywa się to przy użyciu następującego kodu:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Lub można zrobić to samo w konfiguracji:

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) udostępnia bogaty model oparty na oświadczeniach do przeprowadzania kontroli dostępu. Obiekt <xref:System.ServiceModel.ServiceAuthorizationManager> jest używany do wykonywania kontroli dostępu i określić, czy oświadczenia skojarzone z klientem spełniają wymagania niezbędne do uzyskania dostępu do metody usługi.

Na potrzeby demonstracji w tym przykładzie <xref:System.ServiceModel.ServiceAuthorizationManager> przedstawiono implementację, która implementuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę, aby umożliwić `http://example.com/claims/allowedoperation` użytkownikowi dostęp do metod opartych na oświadczeniach typu, którego wartością jest identyfikator URI akcji operacji, która może być wywoływana.

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

Po zaimplementowaniu niestandardowego <xref:System.ServiceModel.ServiceAuthorizationManager> hosta usługi <xref:System.ServiceModel.ServiceAuthorizationManager> musi być informowany o do użycia. Odbywa się to w sposób pokazany w poniższym kodzie.

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Podstawową <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metodą do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> zaimplementowania jest metoda.

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

Poprzedni kod pokazuje, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> jak metoda sprawdza, czy nie dodano żadnych nowych oświadczeń, które wpływają na przetwarzanie i dodaje określone oświadczenia. Oświadczenia, które są dozwolone są `GetAllowedOpList` uzyskiwane z metody, która jest implementowana do zwracania określonej listy operacji, które użytkownik może wykonać. Zasady autoryzacji dodaje oświadczenia dotyczące dostępu do określonej operacji. Jest to później <xref:System.ServiceModel.ServiceAuthorizationManager> używane przez do wykonywania decyzji dotyczących sprawdzania dostępu.

Po zaimplementowaniu niestandardowego <xref:System.IdentityModel.Policy.IAuthorizationPolicy> host usługi musi zostać poinformowany o zasadach autoryzacji do użycia.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie wywołuje Add, Odejmij i wiele metod i pobiera komunikat "Odmowa dostępu" podczas próby wywołania Metody Dzielenia. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

## <a name="setup-batch-file"></a>Plik wsadowy instalatora

Plik wsadowy Setup.bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie, która wymaga zabezpieczeń opartych na certyfikatach serwera.

Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować w celu uruchomienia w odpowiedniej konfiguracji:

- Tworzenie certyfikatu serwera.

    Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany. Zmienna %SERVER_NAME% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartością domyślną jest localhost.

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

    Następujące wiersze w pliku wsadowym Setup.bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Tworzenie certyfikatu klienta.

    Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat klienta, który ma być używany. Zmienna %USER_NAME% określa nazwę serwera. Ta wartość jest ustawiona na "test1", `IAuthorizationPolicy` ponieważ jest to nazwa, która jest wyszukany. Jeśli zmienisz wartość %USER_NAME%, musisz zmienić odpowiednią `IAuthorizationPolicy.Evaluate` wartość w metodzie.

    Certyfikat jest przechowywany w sklepie Mój (osobisty) w lokalizacji sklepu CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu klienta w magazynie zaufanych certyfikatów serwera.

    Następujące wiersze w pliku wsadowym Setup.bat kopiują certyfikat klienta do magazynu zaufanych osób. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system serwera. Jeśli masz już certyfikat, który jest zakorzeniony w zaufanym certyfikacie głównym — na przykład certyfikatowi wystawionemu przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów serwera certyfikatem klienta nie jest wymagany.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i utworzyć próbkę

1. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, należy użyć następujących instrukcji.

> [!NOTE]
> Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić próbkę na tym samym komputerze

1. Otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora i uruchom *plik Setup.bat* z przykładowego folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.

    > [!NOTE]
    > Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dewelopera dla programu Visual Studio. Zmienna środowiskowa PATH ustawiona w wierszu polecenia dewelopera dla programu Visual Studio wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt *Setup.bat.*

1. Uruchom program Service.exe z *pliku service\bin*.

1. Uruchom program Client.exe z *pliku \client\bin*. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.

Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić próbkę na różnych komputerach

1. Utwórz katalog na komputerze usługowym.

2. Skopiuj pliki programu serwisowego z *\service\bin* do katalogu na komputerze usługowym. Skopiuj również pliki Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat do komputera serwisowego.

3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.

4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.

5. Na serwerze `setup.bat service` uruchom w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.

    Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie *Service.cer*.

6. Edytuj *service.exe.config,* aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera. Zmień również **nazwę komputera** \<w serwisie>/\<baseAddresses> element z localhost na w pełni kwalifikowaną nazwę komputera usługowego.

7. Skopiuj plik *Service.cer* z katalogu usługi do katalogu klienta na komputerze klienckim.

8. Na kliencie `setup.bat client` uruchom w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.

    Uruchamianie `setup.bat` `client` z argumentem tworzy certyfikat klienta o nazwie **test1** i eksportuje certyfikat klienta do pliku o nazwie *Client.cer*.

9. W pliku *Client.exe.config* na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi. W tym celu można zastąpić **hosta lokalnego** w pełni kwalifikowaną nazwą domeny serwera.

10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.

11. Na kliencie uruchom *plik ImportServiceCert.bat* w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.

    Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu **CurrentUser — TrustedPeople.**

12. Na serwerze uruchom *plik ImportClientCert.bat* w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.

    Spowoduje to zaimportowanie certyfikatu klienta z pliku Client.cer do magazynu **LocalMachine — TrustedPeople.**

13. Na komputerze serwera uruchom program Service.exe z okna wiersza polecenia.

14. Na komputerze klienckim uruchom program Client.exe z okna wiersza polecenia.

    Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Czyszczenie po próbce

Aby wyczyścić po próbce, uruchom *Cleanup.bat* w folderze próbek po zakończeniu uruchamiania próbki. Spowoduje to usunięcie certyfikatów serwera i klienta z magazynu certyfikatów.

> [!NOTE]
> Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli zostały uruchomione próbki WCF, które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w currentuser — TrustedPeople magazynu. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
