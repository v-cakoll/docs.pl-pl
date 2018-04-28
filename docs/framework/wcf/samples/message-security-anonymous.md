---
title: Zabezpieczenia komunikatów z anonimowością
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
caps.latest.revision: 52
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: c93aacbe5af47c9094dccdaa15828bfa9fda79c5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="message-security-anonymous"></a><span data-ttu-id="20f57-102">Zabezpieczenia komunikatów z anonimowością</span><span class="sxs-lookup"><span data-stu-id="20f57-102">Message Security Anonymous</span></span>
<span data-ttu-id="20f57-103">Komunikat zabezpieczeń anonimowe przykładzie pokazano, jak do zaimplementowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji używającej zabezpieczenia na poziomie komunikatu bez uwierzytelniania klienta, ale który wymaga uwierzytelniania serwera za pomocą certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="20f57-103">The Message Security Anonymous sample demonstrates how to implement a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="20f57-104">Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="20f57-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="20f57-105">Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="20f57-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="20f57-106">W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), obsługiwane przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="20f57-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="20f57-107">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="20f57-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20f57-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="20f57-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="20f57-109">W tym przykładzie dodaje nową operację do interfejsu Kalkulator, która zwraca `True` Jeśli klient nie został uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="20f57-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public bool IsCallerAnonymous()  
    {  
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.  
        return ServiceSecurityContext.Current.IsAnonymous;  
    }  
    ...  
}  
```

 <span data-ttu-id="20f57-110">Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji (Web.config).</span><span class="sxs-lookup"><span data-stu-id="20f57-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="20f57-111">Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="20f57-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="20f57-112">Powiązanie jest skonfigurowane z `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="20f57-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="20f57-113">Domyślny tryb zabezpieczeń `wsHttpBinding` powiązanie to `Message`.</span><span class="sxs-lookup"><span data-stu-id="20f57-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="20f57-114">`clientCredentialType` Atrybut ma ustawioną `None`.</span><span class="sxs-lookup"><span data-stu-id="20f57-114">The `clientCredentialType` attribute is set to `None`.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
     <!--   
     <!--This configuration defines the security mode as Message and-->  
     <!--the clientCredentialType as None. This mode provides -- >  
     <!--server authentication only using the service certificate.-->  
  
     <binding>  
       <security mode="Message">  
         <message clientCredentialType="None" />  
       </security>  
     </binding>  
    </wsHttpBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="20f57-115">Poświadczenia, które mają być używane do uwierzytelniania usługi są określone w [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="20f57-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="20f57-116">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako wartość określona dla `findValue` atrybutu, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="20f57-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>  
      <!--   
    The serviceCredentials behavior allows you to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
    This configuration references the "localhost" certificate installed during the setup instructions.  
    -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
      </serviceCredentials>  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="20f57-117">Konfiguracja punktu końcowego klienta składa się z adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="20f57-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="20f57-118">Tryb zabezpieczeń klienta dla `wsHttpBinding` powiązanie to `Message`.</span><span class="sxs-lookup"><span data-stu-id="20f57-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="20f57-119">`clientCredentialType` Atrybut ma ustawioną `None`.</span><span class="sxs-lookup"><span data-stu-id="20f57-119">The `clientCredentialType` attribute is set to `None`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
             address="http://localhost/servicemodelsamples/service.svc"   
             binding="wsHttpBinding"   
             behaviorConfiguration="ClientCredentialsBehavior"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--This configuration defines the security mode as -->  
      <!--Message and the clientCredentialType as None. -->  
      <binding name="Binding1">  
        <security mode = "Message">  
          <message clientCredentialType="None"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>   
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="20f57-120">Ustawia próbki <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> do <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> do uwierzytelniania certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="20f57-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="20f57-121">Odbywa się w pliku App.config klienta `behaviors` sekcji.</span><span class="sxs-lookup"><span data-stu-id="20f57-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="20f57-122">To oznacza, że jeśli certyfikat znajduje się w magazynie zaufanych osób użytkownika, następnie jest zaufany bez wykonywania sprawdzania poprawności łańcucha wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="20f57-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="20f57-123">To ustawienie jest używane w tym miejscu dla wygody, aby próbki mogą być uruchamiane bez konieczności certyfikatów wystawianych przez urząd certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="20f57-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="20f57-124">To ustawienie jest mniej bezpieczne niż domyślna, ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="20f57-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="20f57-125">Ryzyko związane z tym ustawienie powinien zostać starannie przemyślany przed użyciem `PeerOrChainTrust` w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="20f57-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>  
  
 <span data-ttu-id="20f57-126">Implementacja klienta dodaje wywołanie `IsCallerAnonymous` metody, a w przeciwnym razie nie różni się od [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="20f57-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  

```csharp
// Create a client with a client endpoint configuration.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity operation.  
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
...  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 <span data-ttu-id="20f57-127">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="20f57-128">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
IsCallerAnonymous returned: True  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="20f57-129">Plik wsadowy pliku Setup.bat dołączonego przykładowy komunikat zabezpieczeń anonimowe umożliwia skonfigurowanie serwera przy użyciu odpowiedniego certyfikatu uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="20f57-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="20f57-130">Plik wsadowy może działać w dwóch trybach.</span><span class="sxs-lookup"><span data-stu-id="20f57-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="20f57-131">Aby uruchomić plik wsadowy w trybie pojedynczego komputera, wpisz `setup.bat` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="20f57-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="20f57-132">Aby uruchomić go w trybie usługi, wpisz `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="20f57-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="20f57-133">Uruchamiał ten tryb próbki na komputerach.</span><span class="sxs-lookup"><span data-stu-id="20f57-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="20f57-134">Zapoznaj się z procedurą instalacji na końcu tego tematu, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="20f57-134">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="20f57-135">Poniżej przedstawiono krótkie omówienie różne sekcje pliki wsadowe:</span><span class="sxs-lookup"><span data-stu-id="20f57-135">The following provides a brief overview of the different sections of the batch files:</span></span>  
  
-   <span data-ttu-id="20f57-136">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="20f57-136">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="20f57-137">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="20f57-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="20f57-138">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="20f57-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="20f57-139">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="20f57-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="20f57-140">Jeśli instalacyjny plik wsadowy jest uruchamiana z argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="20f57-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="20f57-141">W przeciwnym razie domyślnie localhost.</span><span class="sxs-lookup"><span data-stu-id="20f57-141">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="20f57-142">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-142">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="20f57-143">Następujący wiersz kopiuje certyfikat serwera w magazynie zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="20f57-144">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="20f57-145">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="20f57-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="20f57-146">Przyznawanie uprawnień do klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="20f57-146">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="20f57-147">Następujące wiersze w pliku wsadowym pliku Setup.bat upewnij przechowywany w magazynie LocalMachine dostępne dla certyfikatu serwera [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] konta procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="20f57-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="20f57-148">Jeśli używasz innej niż stany USA Angielska wersja systemu Windows, należy edytować plik pliku Setup.bat i Zastąp `NT AUTHORITY\NETWORK SERVICE` nazwę konta z Twojej regionalnych równoważne.</span><span class="sxs-lookup"><span data-stu-id="20f57-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20f57-149">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="20f57-149">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="20f57-150">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20f57-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="20f57-151">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20f57-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="20f57-152">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="20f57-152">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="20f57-153">Upewnij się, że ścieżka zawiera folder, w którym znajdują się Makecert.exe i FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="20f57-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="20f57-154">Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki w wierszu polecenia programu Visual Studio uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="20f57-154">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="20f57-155">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="20f57-155">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20f57-156">Instalacyjny plik wsadowy jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="20f57-156">The setup batch file is designed to be run from a  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]Command Prompt.</span></span> <span data-ttu-id="20f57-157">Wymaga, aby zmiennej środowiskowej path punktu do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="20f57-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="20f57-158">Ta zmienna środowiskowa jest ustawiany automatycznie w ramach [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="20f57-158">This environment variable is automatically set within a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]Command Prompt.</span></span>  
  
3.  <span data-ttu-id="20f57-159">Sprawdź dostęp do usługi przy użyciu przeglądarki, wprowadzając adres http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="20f57-159">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="20f57-160">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="20f57-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="20f57-161">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-161">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="20f57-162">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="20f57-162">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="20f57-163">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="20f57-163">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="20f57-164">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="20f57-164">Create a directory on the service computer.</span></span> <span data-ttu-id="20f57-165">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="20f57-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="20f57-166">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="20f57-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="20f57-167">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="20f57-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="20f57-168">Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="20f57-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="20f57-169">Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="20f57-170">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="20f57-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="20f57-171">Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="20f57-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="20f57-172">Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="20f57-172">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="20f57-173">Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="20f57-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="20f57-174">Edytuj plik Web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="20f57-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="20f57-175">Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="20f57-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="20f57-176">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="20f57-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="20f57-177">Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="20f57-177">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="20f57-178">Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="20f57-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="20f57-179">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="20f57-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="20f57-180">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="20f57-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="20f57-181">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="20f57-181">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="20f57-182">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="20f57-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20f57-183">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="20f57-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="20f57-184">Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="20f57-184">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="20f57-185">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="20f57-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f57-186">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20f57-186">See Also</span></span>
