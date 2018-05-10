---
title: Zasady autoryzacji
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 3744afb20c06e1ca85b91dadde6549d87ac89337
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="authorization-policy"></a>Zasady autoryzacji
W tym przykładzie pokazano, jak wdrożyć zasady autoryzacji oświadczeń i skojarzona usługa niestandardowych Menedżera autoryzacji. Jest to przydatne, sprawdza oparta na oświadczeniach dostępu do operacji usługi i przed kontroli dostępu umożliwia usługi przyznaje wywołującego pewne prawa. W tym przykładzie pokazano proces dodawania oświadczeń, a także proces ten kontrolę dostępu przed ukończone zestaw oświadczeń. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane. Domyślnie z `wsHttpBinding` powiązanie, nazwę użytkownika i hasło podane przez klienta są używane do logowania się do prawidłowego konta systemu Windows NT. W tym przykładzie pokazano, jak korzystać z niestandardowego <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` do uwierzytelniania klienta. Ponadto w tym przykładzie pokazano klienta uwierzytelniania w usłudze przy użyciu certyfikatu X.509. Ten przykład przedstawia implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i <xref:System.ServiceModel.ServiceAuthorizationManager>, które między nimi udzielić dostępu do określonych metod usługi dla określonych użytkowników. Ten przykład jest oparty na [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale pokazano, jak wykonać przekształcania oświadczeń, przed <xref:System.ServiceModel.ServiceAuthorizationManager> wywoływane.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Podsumowując, w tym przykładzie pokazano, jak:  
  
-   Klient może zostać uwierzytelniony przy użyciu nazwy — hasło użytkownika.  
  
-   Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.  
  
-   Serwer sprawdza poprawność poświadczeń klienta przed niestandardowego `UsernamePassword` modułu sprawdzania poprawności.  
  
-   Serwer jest uwierzytelniany przy użyciu certyfikat X.509.  
  
-   Serwer może za pomocą <xref:System.ServiceModel.ServiceAuthorizationManager> kontrolować dostęp do pewnych metod w usłudze.  
  
-   Jak zaimplementować <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
 Usługa udostępnia dwa punkty końcowe komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązania i kontrakt. Jedno powiązanie jest skonfigurowane z normą `wsHttpBinding` powiązania, który korzysta z uwierzytelniania nazwa użytkownika WS-Security i klienta. Inne powiązanie jest skonfigurowane z normą `wsHttpBinding` powiązanie użycia uwierzytelniania certyfikatu usługi WS-Security i klienta. [ \<Zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Określa, czy poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` właściwość jako `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
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
  
 Konfiguracja punktu końcowego każdego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu. Powiązanie klienta skonfigurowano tryb zabezpieczeń odpowiednich określone w tym przypadku w [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) i `clientCredentialType` jak określono w [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).  
  
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
  
 Dla użytkownika na podstawie nazwy punktu końcowego implementacja klienta ustawia nazwę użytkownika i hasło do użycia.  
  
```  
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
  
 Dla punktu końcowego na podstawie certyfikatu implementacja klienta ustawia certyfikat klienta do użycia.  
  
```  
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
  
 Ten przykład używa niestandardowej <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> do sprawdzania poprawności nazwy użytkownika i hasła. Implementuje próbki `MyCustomUserNamePasswordValidator`, pochodną <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Można znaleźć w dokumentacji <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Aby uzyskać więcej informacji. Na potrzeby demonstrowania integracji z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, w tym przykładzie niestandardowego modułu weryfikacji implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę, aby zaakceptować pary nazwa/hasło użytkownika, jeśli nazwa użytkownika odpowiada hasło, jak pokazano w poniższym kodzie.  
  
```  
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
  
 Po zaimplementowaniu w kodzie usługi modułu sprawdzania poprawności hosta usługi musi informację o wystąpienia modułu sprawdzania poprawności do użycia. Jest to realizowane przy użyciu następującego kodu.  
  
```  
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();  
```  
  
 Lub może tak samo postąpić w konfiguracji.  
  
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
  
 Windows Communication Foundation (WCF) zapewnia zaawansowane modelu opartego na oświadczeniach do wykonywania kontroli dostępu. <xref:System.ServiceModel.ServiceAuthorizationManager> Obiekt jest używany do wykonywania kontroli dostępu i ustalić, czy oświadczeń skojarzone z klientami spełniają wymagania niezbędne do uzyskania dostępu do metody usługi.  
  
 Dla celów demonstracyjnych, w tym przykładzie pokazano implementacja <xref:System.ServiceModel.ServiceAuthorizationManager> implementującej <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę, aby zezwolić na dostęp użytkownika do metod na podstawie oświadczeń typu http://example.com/claims/allowedoperation którego wartość jest identyfikatorem URI akcji działania, który jest może zostać wywołana.  
  
```  
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
  
 Raz niestandardowego <xref:System.ServiceModel.ServiceAuthorizationManager> jest zaimplementowana, hosta usługi musi być poinformowani o <xref:System.ServiceModel.ServiceAuthorizationManager> do użycia. Jest to, jak pokazano w poniższym kodzie.  
  
```xml  
<behavior ...>  
    ...  
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
        ...  
    </serviceAuthorization>  
</behavior>  
```  
  
 Podstawowy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metodą wykonania jest <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody.  
  
```  
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
  
 W poprzednim kodzie jak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda sprawdza, czy nie nowych oświadczeń zostały dodane, które wpływają na przetwarzanie i dodaje określonych oświadczeń. Oświadczenia, które są dozwolone są uzyskiwane z `GetAllowedOpList` metodę, która jest zaimplementowana, aby zwrócić listę działań, które użytkownik może wykonywać. Zasady autoryzacji dodaje oświadczenia do uzyskiwania dostępu do określonej operacji. To jest później używany przez <xref:System.ServiceModel.ServiceAuthorizationManager> przeprowadzić decyzje dotyczące kontroli dostępu.  
  
 Raz niestandardowego <xref:System.IdentityModel.Policy.IAuthorizationPolicy> zaimplementowaniu hosta usługi musi być informację o zasady autoryzacji do użycia.  
  
```xml  
<serviceAuthorization ...>  
       <authorizationPolicies>   
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />  
       </authorizationPolicies>   
</serviceAuthorization>  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie wywołuje Add i Subtract wiele metod i pobiera komunikat "Odmowa dostępu" podczas próby wywołania metody dzielenia. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera.  
  
 Poniżej przedstawiono krótkie omówienie różne sekcje pliki wsadowe, tak, aby można modyfikować w prawidłowej konfiguracji:  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. % Zmienna % nazwa_serwera Określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Wartość domyślna to localhost.  
  
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
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty, które są generowane przez Makecert.exe niejawnie są nie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Tworzenie certyfikatu klienta.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat Utwórz certyfikat klienta, który ma być używany. % Zmienna % nazwa_użytkownika Określa nazwę serwera. Ta wartość jest równa "test1", ponieważ jest to nazwa `IAuthorizationPolicy` szuka. W przypadku zmiany wartości nazwa_użytkownika % należy zmienić odpowiednie wartości w `IAuthorizationPolicy.Evaluate` metody.  
  
     Certyfikat jest przechowywany w magazynie My (osobistych) w lokalizacji w magazynie CurrentUser.  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.  
  
     Następujące wiersze w pliku wsadowym pliku Setup.bat skopiuj certyfikat klienta w magazynie zaufanych osób. Ten krok jest wymagany, ponieważ certyfikaty, które są generowane przez Makecert.exe niejawnie są nie ufa systemu serwera. Jeśli masz już certyfikatu, który jest ścieżką do katalogu głównego w zaufanym certyfikatem głównym — na przykład certyfikat wystawiony Microsoft — ten krok zapełnianie magazynu certyfikatów na serwerze przy użyciu certyfikatu klienta nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, użyj poniższych instrukcji.  
  
> [!NOTE]
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] okno wiersza polecenia z uprawnieniami administratora i wykonywania pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
2.  Uruchamianie pliku Setup.bat w programie Visual Studio wiersza polecenia otwartym z uprawnieniami administratora z próbki folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
3.  Uruchom Service.exe z service\bin.  
  
4.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
5.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi.  
  
2.  Skopiuj pliki programu usługi z \service\bin do katalogu na komputerze usługi. Także skopiować pliki pliku Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat na komputerze usługi.  
  
3.  Utwórz katalog na computerfor klienta pliki binarne klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę eksportu computerand certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj Service.exe.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera. Również zmienić właściwości computername w \<usługi > /\<baseAddresses > elementu localhost pełną nazwę komputera usługi.  
  
7.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
8.  Na komputerze klienckim, uruchom `setup.bat client` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie test1 i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi. W tym celu zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
12. Na serwerze należy uruchomić ImportClientCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat klienta to importuje z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
13. Na komputerze serwera Uruchom Service.exe z okna wiersza polecenia.  
  
14. Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki. Spowoduje to usunięcie certyfikaty serwera i klienta z magazynu certyfikatów.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Po uruchomieniu przykłady WCF, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople przechowywania. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też
