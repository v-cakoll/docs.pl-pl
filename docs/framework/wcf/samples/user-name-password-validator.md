---
title: "Moduł weryfikacji nazwy użytkownika i hasła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 627670c989510bd82e4d9b6aa7550476be1ce750
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="user-name-password-validator"></a><span data-ttu-id="35768-102">Moduł weryfikacji nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="35768-102">User Name Password Validator</span></span>
<span data-ttu-id="35768-103">W tym przykładzie pokazano, jak do zaimplementowania niestandardowego modułu weryfikacji UserNamePassword.</span><span class="sxs-lookup"><span data-stu-id="35768-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="35768-104">Jest to przydatne w sytuacjach, gdy żaden z wbudowanych tryby UserNamePassword sprawdzania poprawności nie jest odpowiednią do wymagań aplikacji; na przykład gdy pary nazwa użytkownika i hasło są przechowywane w magazynie zewnętrznym, takie jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="35768-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="35768-105">W tym przykładzie pokazano usługi, która ma niestandardowego modułu weryfikacji, który sprawdza, czy dwie pary określonej nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="35768-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="35768-106">Klient używa parę nazwy użytkownika i hasła do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="35768-106">The client uses such a username/password pair to authenticate to the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="35768-107">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="35768-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="35768-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="35768-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="35768-109">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="35768-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35768-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="35768-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  <span data-ttu-id="35768-111">Ponieważ każdy można konstruować poświadczeniami nazwy użytkownika, które używa par nazwa użytkownika i hasło, które akceptuje niestandardowego modułu weryfikacji, usługa jest mniej bezpieczna niż udostępniane przez moduł sprawdzania poprawności UserNamePassword standardowe zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="35768-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="35768-112">Standardowy moduł sprawdzania poprawności UserNamePassword próbuje zamapować pary podana nazwa użytkownika/hasło do konta systemu Windows i niepowodzenia uwierzytelniania, jeśli to mapowanie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="35768-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="35768-113">Niestandardowe, które moduł sprawdzania poprawności UserNamePassword w tym przykładzie nie mogą być używane w kodzie produkcyjnym, jest wyłącznie dla celów ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="35768-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>  
  
 <span data-ttu-id="35768-114">W podsumowaniu przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="35768-114">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="35768-115">Klient może zostać uwierzytelniony przy użyciu tokenu nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="35768-115">The client can be authenticated using a Username Token.</span></span>  
  
-   <span data-ttu-id="35768-116">Serwer sprawdza poprawność poświadczeń klienta przed UserNamePasswordValidator niestandardowych i jak Propagacja błędów niestandardowych z logiki sprawdzania poprawności nazwy użytkownika i hasła do klienta.</span><span class="sxs-lookup"><span data-stu-id="35768-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>  
  
-   <span data-ttu-id="35768-117">Serwer jest uwierzytelniany przy użyciu certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="35768-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="35768-118">Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="35768-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="35768-119">Powiązanie jest skonfigurowane z normą `wsHttpBinding` który domyślnie korzysta z protokołu WS-Securityand uwierzytelniania nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="35768-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Securityand username authentication.</span></span> <span data-ttu-id="35768-120">Określa zachowanie usługi `Custom` tryb dla weryfikacji klienta pary nazwy użytkownika i hasła oraz typ klasy modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="35768-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="35768-121">Zachowanie określa również przy użyciu certyfikatu serwera `serviceCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="35768-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="35768-122">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="35768-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="35768-123">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="35768-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="35768-124">Klient powiązanie jest skonfigurowane przy użyciu odpowiedni tryb i komunikat `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="35768-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="35768-125">Implementacja klienta monituje użytkownika o wprowadzenie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="35768-125">The client implementation prompts the user to enter a username and password.</span></span>  
  
```  
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
  
 <span data-ttu-id="35768-126">W przykładzie użyto niestandardowego UserNamePasswordValidator do zweryfikowania par nazwa użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="35768-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="35768-127">Implementuje próbki `CustomUserNamePasswordValidator`, pochodną <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="35768-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="35768-128">Zajrzyj do dokumentacji <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="35768-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="35768-129">W tym przykładzie niestandardowego modułu sprawdzania poprawności implementuje `Validate` metodę, aby zaakceptować dwie pary określonej nazwy użytkownika i hasła, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="35768-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="35768-130">Po zaimplementowaniu w kodzie usługi modułu sprawdzania poprawności hosta usługi musi informację o wystąpienia modułu sprawdzania poprawności do użycia.</span><span class="sxs-lookup"><span data-stu-id="35768-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="35768-131">Jest to realizowane przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="35768-131">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();  
```  
  
 <span data-ttu-id="35768-132">Lub tak samo postąpić w konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="35768-132">Or you can do the same thing in configuration as follows.</span></span>  
  
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
  
 <span data-ttu-id="35768-133">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="35768-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="35768-134">Klient pomyślnie powinny wywoływać wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="35768-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="35768-135">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="35768-135">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="35768-136">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="35768-136">Setup Batch File</span></span>  
 <span data-ttu-id="35768-137">Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="35768-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="35768-138">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku hostowanych samoobsługowego.</span><span class="sxs-lookup"><span data-stu-id="35768-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>  
  
 <span data-ttu-id="35768-139">Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35768-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="35768-140">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="35768-140">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="35768-141">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="35768-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="35768-142">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="35768-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="35768-143">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="35768-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="35768-144">Wartość domyślna to localhost.</span><span class="sxs-lookup"><span data-stu-id="35768-144">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="35768-145">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="35768-145">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="35768-146">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="35768-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="35768-147">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="35768-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="35768-148">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="35768-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="35768-149">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="35768-149">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="35768-150">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35768-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="35768-151">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="35768-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="35768-152">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="35768-152">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="35768-153">Uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35768-153">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt.</span></span> <span data-ttu-id="35768-154">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="35768-154">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35768-155">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35768-155">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="35768-156">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35768-156">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="35768-157">Uruchom Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="35768-157">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="35768-158">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="35768-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="35768-159">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="35768-159">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="35768-160">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="35768-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="35768-161">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="35768-161">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="35768-162">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="35768-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="35768-163">Skopiuj pliki programu usługi katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="35768-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="35768-164">Także skopiować pliki pliku Setup.bat i Cleanup.bat maszynie usługi.</span><span class="sxs-lookup"><span data-stu-id="35768-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="35768-165">Wymagany jest certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny maszyny.</span><span class="sxs-lookup"><span data-stu-id="35768-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="35768-166">Plik konfiguracji serwera musi zaktualizować w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="35768-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4.  <span data-ttu-id="35768-167">Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="35768-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="35768-168">Należy to zrobić tylko, jeśli certyfikat serwera nie jest wystawiany przez zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="35768-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="35768-169">W pliku App.config na komputerze usługi Zmień wartość adres bazowy, określ nazwę maszyny w pełni kwalifikowaną zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="35768-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="35768-170">Na komputerze usługi uruchom Service.exe z poziomu okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35768-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7.  <span data-ttu-id="35768-171">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="35768-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8.  <span data-ttu-id="35768-172">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="35768-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="35768-173">Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="35768-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="35768-174">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="35768-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="35768-175">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="35768-175">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="35768-176">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="35768-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="35768-177">Spowoduje to usunięcie certyfikatu serwera z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="35768-177">This removes the server certificate from the certificate store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35768-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35768-178">See Also</span></span>
