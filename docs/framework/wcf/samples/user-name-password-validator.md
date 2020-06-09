---
title: Moduł weryfikacji nazwy użytkownika i hasła
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 5fbca30ef2dff0aebc13bda12c06adfd1989ea20
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596516"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="936c5-102">Moduł weryfikacji nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="936c5-102">User Name Password Validator</span></span>
<span data-ttu-id="936c5-103">Ten przykład pokazuje, jak wdrożyć niestandardowy moduł sprawdzania poprawności UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="936c5-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="936c5-104">Jest to przydatne w przypadkach, gdy żaden z wbudowanych trybów weryfikacji UserNamePassword nie jest odpowiedni dla wymagań aplikacji. na przykład, gdy pary username i Password są przechowywane w niektórych magazynach zewnętrznych, takich jak baza danych.</span><span class="sxs-lookup"><span data-stu-id="936c5-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="936c5-105">Ten przykład pokazuje usługę, która ma niestandardowy moduł sprawdzania poprawności, który sprawdza dwie konkretne pary nazw użytkownika/hasła.</span><span class="sxs-lookup"><span data-stu-id="936c5-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="936c5-106">Klient używa pary nazwa użytkownika/hasło do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="936c5-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="936c5-107">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="936c5-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="936c5-108">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="936c5-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="936c5-109">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="936c5-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="936c5-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="936c5-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="936c5-111">Ponieważ każda osoba może utworzyć poświadczenia nazwy użytkownika, która używa par username/Password, które akceptuje niestandardowy moduł walidacji, usługa jest mniej bezpieczna niż domyślne zachowanie udostępniane przez standardowy moduł UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="936c5-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="936c5-112">Standardowy moduł sprawdzania poprawności UserNamePassword próbuje zmapować podanej pary nazwa użytkownika/hasło na konto systemu Windows i niepowodzenie uwierzytelniania w przypadku niepowodzenia tego mapowania.</span><span class="sxs-lookup"><span data-stu-id="936c5-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="936c5-113">Niestandardowego modułu sprawdzania UserNamePassword w tym przykładzie nie można używać w kodzie produkcyjnym, tylko do celów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="936c5-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="936c5-114">W podsumowaniu ten przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="936c5-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="936c5-115">Klienta można uwierzytelnić przy użyciu tokenu nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="936c5-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="936c5-116">Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego UserNamePasswordValidator i sposób propagowania błędów niestandardowych z logiki weryfikacji nazwy użytkownika i hasła do klienta.</span><span class="sxs-lookup"><span data-stu-id="936c5-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="936c5-117">Serwer jest uwierzytelniany przy użyciu certyfikatu X. 509 serwera.</span><span class="sxs-lookup"><span data-stu-id="936c5-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="936c5-118">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji, App. config. Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="936c5-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="936c5-119">Powiązanie jest skonfigurowane ze standardem `wsHttpBinding` , który domyślnie używa uwierzytelniania WS-Security i username.</span><span class="sxs-lookup"><span data-stu-id="936c5-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="936c5-120">Zachowanie usługi określa `Custom` tryb weryfikacji par nazwy użytkownika/hasła klienta wraz z typem klasy modułu walidacji.</span><span class="sxs-lookup"><span data-stu-id="936c5-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="936c5-121">Zachowanie określa również certyfikat serwera za pomocą `serviceCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="936c5-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="936c5-122">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jak `findValue` w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="936c5-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="936c5-123">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="936c5-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="936c5-124">Powiązanie klienta jest skonfigurowane z odpowiednim trybem i komunikatem `clientCredentialType` .</span><span class="sxs-lookup"><span data-stu-id="936c5-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="936c5-125">Implementacja klienta prosi użytkownika o podanie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="936c5-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="936c5-126">Ten przykład używa niestandardowego UserNamePasswordValidator do sprawdzania poprawności par nazw i haseł.</span><span class="sxs-lookup"><span data-stu-id="936c5-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="936c5-127">Przykład implementuje `CustomUserNamePasswordValidator` , pochodny od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="936c5-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="936c5-128"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator>Aby uzyskać więcej informacji, zobacz dokumentację.</span><span class="sxs-lookup"><span data-stu-id="936c5-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="936c5-129">Ten konkretny niestandardowy przykład modułu sprawdzania poprawności implementuje `Validate` metodę, aby akceptować dwie konkretne pary nazwy użytkownika/hasła, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="936c5-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="936c5-130">Po wdrożeniu modułu sprawdzania poprawności w kodzie usługi Host usługi musi zostać poinformowany o wystąpieniu modułu sprawdzania poprawności, które ma być używane.</span><span class="sxs-lookup"><span data-stu-id="936c5-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="936c5-131">Jest to realizowane przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="936c5-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="936c5-132">Można też wykonać tę czynność w konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="936c5-132">Or you can do the same thing in configuration as follows.</span></span>

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
   </serviceCredentials>
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="936c5-133">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="936c5-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="936c5-134">Klient powinien pomyślnie wywołać wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="936c5-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="936c5-135">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="936c5-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="936c5-136">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="936c5-136">Setup Batch File</span></span>
 <span data-ttu-id="936c5-137">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="936c5-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="936c5-138">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych maszynach lub działać w niezależnym przypadku.</span><span class="sxs-lookup"><span data-stu-id="936c5-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="936c5-139">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="936c5-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="936c5-140">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="936c5-140">Creating the server certificate:</span></span>

     <span data-ttu-id="936c5-141">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="936c5-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="936c5-142">Zmienna% SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="936c5-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="936c5-143">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="936c5-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="936c5-144">Wartość domyślna to localhost.</span><span class="sxs-lookup"><span data-stu-id="936c5-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="936c5-145">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="936c5-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="936c5-146">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="936c5-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="936c5-147">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="936c5-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="936c5-148">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="936c5-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="936c5-149">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="936c5-149">To set up and build the sample</span></span>

1. <span data-ttu-id="936c5-150">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="936c5-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="936c5-151">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.</span><span class="sxs-lookup"><span data-stu-id="936c5-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="936c5-152">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="936c5-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="936c5-153">Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="936c5-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="936c5-154">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="936c5-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="936c5-155">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="936c5-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="936c5-156">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="936c5-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="936c5-157">Uruchom usługę Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="936c5-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="936c5-158">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="936c5-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="936c5-159">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="936c5-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="936c5-160">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="936c5-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="936c5-161">Aby uruchomić przykład na wielu maszynach</span><span class="sxs-lookup"><span data-stu-id="936c5-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="936c5-162">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="936c5-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="936c5-163">Skopiuj program Service Files do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="936c5-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="936c5-164">Skopiuj także pliki Setup. bat i Oczyść. bat do maszyny usługi.</span><span class="sxs-lookup"><span data-stu-id="936c5-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="936c5-165">Potrzebny jest certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="936c5-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="936c5-166">Plik konfiguracji dla serwera musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="936c5-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="936c5-167">Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="936c5-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="936c5-168">Należy to zrobić tylko wtedy, gdy certyfikat serwera nie zostanie wystawiony przez zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="936c5-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="936c5-169">W pliku App. config na komputerze usługi Zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="936c5-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="936c5-170">Na komputerze usługi Uruchom program Service. exe w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="936c5-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="936c5-171">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="936c5-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="936c5-172">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="936c5-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="936c5-173">Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="936c5-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="936c5-174">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="936c5-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="936c5-175">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="936c5-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="936c5-176">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="936c5-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="936c5-177">Spowoduje to usunięcie certyfikatu serwera z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="936c5-177">This removes the server certificate from the certificate store.</span></span>  
