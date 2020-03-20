---
title: Nazwa użytkownika zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183510"
---
# <a name="message-security-user-name"></a><span data-ttu-id="1a8fd-102">Nazwa użytkownika zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="1a8fd-102">Message Security User Name</span></span>
<span data-ttu-id="1a8fd-103">W tym przykładzie pokazano, jak zaimplementować aplikację, która używa programu WS-Security z uwierzytelnianiem nazwy użytkownika dla klienta i wymaga uwierzytelnienia serwera przy użyciu certyfikatu X.509v3 serwera.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="1a8fd-104">Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="1a8fd-105">Domyślnie nazwa użytkownika i hasło dostarczone przez klienta są używane do logowania do prawidłowego konta systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="1a8fd-106">Ten przykład jest oparty na [programie WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="1a8fd-107">Ten przykład składa się z programu konsoli klienta (Client.exe) i biblioteki usług (Service.dll) hostowanych przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="1a8fd-108">Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a8fd-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1a8fd-110">W tym przykładzie pokazano również:</span><span class="sxs-lookup"><span data-stu-id="1a8fd-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="1a8fd-111">Domyślne mapowanie do kont systemu Windows, dzięki czemu można wykonać dodatkową autoryzację.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="1a8fd-112">Jak uzyskać dostęp do informacji o tożsamości wywołującego z kodu usługi.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="1a8fd-113">Usługa udostępnia jeden punkt końcowy do komunikowania się z usługą, który jest zdefiniowany przy użyciu pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="1a8fd-114">Powiązanie jest skonfigurowane ze standardem [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), który domyślnie używa zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="1a8fd-115">W tym przykładzie ustawia standardowy [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do używania uwierzytelniania nazwy użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="1a8fd-116">Zachowanie określa, że poświadczenia użytkownika mają być używane do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="1a8fd-117">Certyfikat serwera musi zawierać taką samą wartość `findValue` dla nazwy podmiotu, jak atrybut w [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
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
</system.serviceModel>  
```  
  
 <span data-ttu-id="1a8fd-118">Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="1a8fd-119">Powiązanie klienta jest skonfigurowane `securityMode` `authenticationMode`z odpowiednimi i .</span><span class="sxs-lookup"><span data-stu-id="1a8fd-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="1a8fd-120">Podczas uruchamiania w scenariuszu między komputerami, adres punktu końcowego usługi musi zostać odpowiednio zmieniony.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1a8fd-121">Implementacja klienta ustawia nazwę użytkownika i hasło do użycia.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="1a8fd-122">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1a8fd-123">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1a8fd-124">Plik wsadowy Setup.bat dołączony do przykładów MessageSecurity umożliwia skonfigurowanie serwera z odpowiednim certyfikatem do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="1a8fd-125">Plik wsadowy można uruchomić w dwóch trybach.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="1a8fd-126">Aby uruchomić plik wsadowy w trybie jednokomputerowym, wpisz `setup.bat` wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="1a8fd-127">Aby uruchomić go w `setup.bat service`trybie serwisowym typu .</span><span class="sxs-lookup"><span data-stu-id="1a8fd-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="1a8fd-128">Ten tryb jest używany podczas uruchamiania próbki na komputerach.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="1a8fd-129">Szczegółowe informacje można znaleźć w procedurze konfiguracji na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="1a8fd-130">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="1a8fd-131">Tworzenie certyfikatu serwera</span><span class="sxs-lookup"><span data-stu-id="1a8fd-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="1a8fd-132">Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="1a8fd-133">Zmienna %SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="1a8fd-134">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="1a8fd-135">Jeśli plik wsadowy Setup.bat jest uruchamiany `setup.bat service`z argumentem usługi (na przykład ) %SERVER_NAME% zawiera w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="1a8fd-136">W przeciwnym razie domyślnie localhost.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="1a8fd-137">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="1a8fd-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="1a8fd-138">Poniższy wiersz kopiuje certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1a8fd-139">Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1a8fd-140">Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="1a8fd-141">Udzielanie uprawnień do klucza prywatnego certyfikatu</span><span class="sxs-lookup"><span data-stu-id="1a8fd-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="1a8fd-142">Następujące wiersze w pliku wsadowym Setup.bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu ASP.NET procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="1a8fd-143">Jeśli używasz wersji systemu Windows w wersji systemu Windows innej niż amerykańska, `NT AUTHORITY\NETWORK SERVICE` musisz edytować plik Setup.bat i zastąpić nazwę konta regionalnym odpowiednikiem.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a8fd-144">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="1a8fd-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1a8fd-145">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1a8fd-146">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1a8fd-147">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="1a8fd-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="1a8fd-148">Upewnij się, że ścieżka zawiera folder, w którym znajdują się pliki Makecert.exe i FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="1a8fd-149">Uruchom plik Setup.bat z przykładowego folderu instalacji w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="1a8fd-150">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1a8fd-151">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dewelopera dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="1a8fd-152">Wymaga, aby zmienna środowiskowa ścieżki wskazywała katalog, w którym jest zainstalowany pakiet SDK.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1a8fd-153">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia dewelopera dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="1a8fd-154">Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="1a8fd-155">Uruchom program Client.exe z pliku \client\bin.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="1a8fd-156">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="1a8fd-157">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1a8fd-158">Aby uruchomić próbkę na różnych komputerach</span><span class="sxs-lookup"><span data-stu-id="1a8fd-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="1a8fd-159">Utwórz katalog na komputerze usługowym.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-159">Create a directory on the service computer.</span></span> <span data-ttu-id="1a8fd-160">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania internetowymi usługami informacyjnymi.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="1a8fd-161">Skopiuj pliki programu serwisowego z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="1a8fd-162">Upewnij się, że pliki są kopiowane w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="1a8fd-163">Skopiuj również pliki Setup.bat i Cleanup.bat do komputera serwisowego.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="1a8fd-164">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="1a8fd-165">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="1a8fd-166">Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="1a8fd-167">Na serwerze `setup.bat service` uruchom w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="1a8fd-168">Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="1a8fd-169">Edytuj web.config, aby odzwierciedlić nową nazwę certyfikatu (w findValue atrybut w serviceCertificate element), który jest taki sam jak w pełni kwalifikowana nazwa domeny komputera`.`</span><span class="sxs-lookup"><span data-stu-id="1a8fd-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="1a8fd-170">Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="1a8fd-171">W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="1a8fd-172">Na kliencie uruchom plik ImportServiceCert.bat w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="1a8fd-173">Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="1a8fd-174">Na komputerze klienckim uruchom program Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="1a8fd-175">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1a8fd-176">Aby oczyścić po próbce</span><span class="sxs-lookup"><span data-stu-id="1a8fd-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="1a8fd-177">Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1a8fd-178">Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="1a8fd-179">Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="1a8fd-180">Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
