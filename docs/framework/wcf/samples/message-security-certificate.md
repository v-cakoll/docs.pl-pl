---
title: Certyfikat zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 92e656f36ae0af851def393575cbb7d418bc4a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183533"
---
# <a name="message-security-certificate"></a><span data-ttu-id="1c75d-102">Certyfikat zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="1c75d-102">Message Security Certificate</span></span>
<span data-ttu-id="1c75d-103">W tym przykładzie pokazano, jak zaimplementować aplikację, która używa programu WS-Security z uwierzytelnianiem certyfikatu X.509 v3 dla klienta i wymaga uwierzytelnienia serwera przy użyciu certyfikatu X.509 v3 serwera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="1c75d-104">W tym przykładzie użyto ustawień domyślnych, takich jak, że wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="1c75d-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="1c75d-105">Ten przykład jest oparty na [programie WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) i składa się z programu konsoli klienta i biblioteki usług hostowanych przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="1c75d-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="1c75d-106">Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="1c75d-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c75d-107">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1c75d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1c75d-108">Przykład pokazuje kontrolowanie uwierzytelniania przy użyciu konfiguracji i jak uzyskać tożsamość wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c75d-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="1c75d-109">Usługa udostępnia jeden punkt końcowy do komunikowania się z usługą i jeden punkt końcowy do udostępnienia dokumentu WSDL usługi przy użyciu protokołu WS-MetadataExchange, zdefiniowane przy użyciu pliku konfiguracyjnego (Web.config).</span><span class="sxs-lookup"><span data-stu-id="1c75d-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="1c75d-110">Punkt końcowy składa się z adresu, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="1c75d-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="1c75d-111">Powiązanie jest skonfigurowane ze standardowym [ \<elementem>wsHttpBinding,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) który domyślnie używa zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1c75d-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="1c75d-112">W tym `clientCredentialType` przykładzie ustawia atrybut Certyfikat, aby wymagać uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
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
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="1c75d-113">Zachowanie określa poświadczenia usługi, które są używane, gdy klient uwierzytelnia usługę.</span><span class="sxs-lookup"><span data-stu-id="1c75d-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="1c75d-114">Nazwa podmiotu certyfikatu serwera `findValue` jest określona w atrybucie w [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span><span class="sxs-lookup"><span data-stu-id="1c75d-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
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
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="1c75d-115">Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="1c75d-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="1c75d-116">Powiązanie klienta jest skonfigurowane przy użyciu odpowiedniego trybu zabezpieczeń i trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1c75d-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="1c75d-117">Podczas uruchamiania w scenariuszu między komputerami, upewnij się, że adres punktu końcowego usługi zostanie odpowiednio zmieniony.</span><span class="sxs-lookup"><span data-stu-id="1c75d-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1c75d-118">Implementacja klienta można ustawić certyfikat do użycia, za pośrednictwem pliku konfiguracji lub za pośrednictwem kodu.</span><span class="sxs-lookup"><span data-stu-id="1c75d-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="1c75d-119">W poniższym przykładzie pokazano, jak ustawić certyfikat do użycia w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="1c75d-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1c75d-120">W poniższym przykładzie pokazano, jak wywołać usługę w programie.</span><span class="sxs-lookup"><span data-stu-id="1c75d-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="1c75d-121">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1c75d-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="1c75d-123">Plik wsadowy Setup.bat dołączony do przykładów zabezpieczeń wiadomości umożliwia skonfigurowanie klienta i serwera z odpowiednimi certyfikatami do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="1c75d-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="1c75d-124">Plik wsadowy można uruchomić w trzech trybach.</span><span class="sxs-lookup"><span data-stu-id="1c75d-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="1c75d-125">Aby uruchomić w trybie jednokomunijnym typu **setup.bat** w wierszu polecenia dewelopera dla programu Visual Studio ; dla usługi typu **setup.bat**w trybie serwisowym ; i dla klienta typu **setup.bat klienta**.</span><span class="sxs-lookup"><span data-stu-id="1c75d-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="1c75d-126">Użyj trybu klienta i serwera podczas uruchamiania próbki na komputerach.</span><span class="sxs-lookup"><span data-stu-id="1c75d-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="1c75d-127">Szczegółowe informacje można znaleźć w procedurze konfiguracji na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1c75d-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="1c75d-128">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować w celu uruchomienia w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="1c75d-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="1c75d-129">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="1c75d-130">Następujący wiersz w pliku wsadowym tworzy certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="1c75d-131">Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1c75d-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="1c75d-132">Certyfikat jest przechowywany `My` w `CurrentUser` magazynie w lokalizacji sklepu.</span><span class="sxs-lookup"><span data-stu-id="1c75d-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="1c75d-133">Instalowanie certyfikatu klienta w magazynie certyfikatów zaufanych serwera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="1c75d-134">Poniższy wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje dotyczące zaufania lub braku zaufania.</span><span class="sxs-lookup"><span data-stu-id="1c75d-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="1c75d-135">Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), należy `PeerOrChainTrust` ustawić `PeerTrust`tryb sprawdzania poprawności certyfikatu klienta lub .</span><span class="sxs-lookup"><span data-stu-id="1c75d-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="1c75d-136">Zobacz przykład poprzedniej konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="1c75d-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- <span data-ttu-id="1c75d-137">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="1c75d-138">Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="1c75d-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="1c75d-139">Zmienna %SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="1c75d-140">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1c75d-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="1c75d-141">Jeśli plik wsadowy Setup.bat jest uruchamiany z argumentem usługi (takim jak **usługa setup.bat),**%SERVER_NAME% zawiera w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="1c75d-142">W przeciwnym razie domyślnie localhost.</span><span class="sxs-lookup"><span data-stu-id="1c75d-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="1c75d-143">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="1c75d-144">Poniższy wiersz kopiuje certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1c75d-145">Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki.</span><span class="sxs-lookup"><span data-stu-id="1c75d-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1c75d-146">Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="1c75d-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="1c75d-147">Udzielanie uprawnień do klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1c75d-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="1c75d-148">Następujące wiersze w pliku Setup.bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu ASP.NET procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="1c75d-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="1c75d-149">Jeśli używasz wersji systemu Windows w języku niesie poza USA, musisz edytować plik Setup.bat i zastąpić nazwę konta "NT AUTHORITY\NETWORK SERVICE" regionalnym odpowiednikiem.</span><span class="sxs-lookup"><span data-stu-id="1c75d-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c75d-150">Narzędzia używane w tym pliku wsadowym znajdują się w folderze C:\Program Files\Microsoft Visual Studio 8\Common7\tools lub C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="1c75d-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="1c75d-151">Jeden z tych katalogów musi znajdować się w ścieżce systemowej.</span><span class="sxs-lookup"><span data-stu-id="1c75d-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="1c75d-152">Jeśli masz zainstalowany program Visual Studio, najprostszym sposobem, aby uzyskać ten katalog w ścieżce jest otwarcie wiersza polecenia dewelopera dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c75d-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="1c75d-153">Kliknij **przycisk Start**, a następnie wybierz pozycję Wszystkie **programy**, **Visual Studio 2012**, **Narzędzia**.</span><span class="sxs-lookup"><span data-stu-id="1c75d-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="1c75d-154">Ten wiersz polecenia ma już skonfigurowane odpowiednie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="1c75d-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="1c75d-155">W przeciwnym razie należy ręcznie dodać odpowiedni katalog do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="1c75d-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1c75d-156">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1c75d-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1c75d-157">Przed kontynuowaniem sprawdź następujący (domyślny) katalog:</span><span class="sxs-lookup"><span data-stu-id="1c75d-157">Check for the following (default) directory before continuing:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1c75d-158">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="1c75d-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1c75d-159">Ten przykład znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="1c75d-159">This sample is located in the following directory:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1c75d-160">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="1c75d-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1c75d-161">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1c75d-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1c75d-162">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1c75d-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1c75d-163">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="1c75d-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="1c75d-164">Otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora i uruchom plik Setup.bat z przykładowego folderu instalacji.</span><span class="sxs-lookup"><span data-stu-id="1c75d-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="1c75d-165">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.</span><span class="sxs-lookup"><span data-stu-id="1c75d-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1c75d-166">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dewelopera dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c75d-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="1c75d-167">Wymaga, aby zmienna środowiskowa ścieżki wskazywała katalog, w którym jest zainstalowany pakiet SDK.</span><span class="sxs-lookup"><span data-stu-id="1c75d-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1c75d-168">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia dewelopera dla programu Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="1c75d-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="1c75d-169">Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="1c75d-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="1c75d-170">Uruchom program Client.exe z pliku \client\bin.</span><span class="sxs-lookup"><span data-stu-id="1c75d-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="1c75d-171">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="1c75d-172">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1c75d-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1c75d-173">Aby uruchomić próbkę na różnych komputerach</span><span class="sxs-lookup"><span data-stu-id="1c75d-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="1c75d-174">Utwórz katalog na komputerze usługowym.</span><span class="sxs-lookup"><span data-stu-id="1c75d-174">Create a directory on the service computer.</span></span> <span data-ttu-id="1c75d-175">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania internetowymi usługami informacyjnymi (IIS).</span><span class="sxs-lookup"><span data-stu-id="1c75d-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="1c75d-176">Skopiuj pliki programu serwisowego z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="1c75d-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="1c75d-177">Upewnij się, że pliki są kopiowane w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="1c75d-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="1c75d-178">Skopiuj również pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na komputer usługi.</span><span class="sxs-lookup"><span data-stu-id="1c75d-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="1c75d-179">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="1c75d-180">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1c75d-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="1c75d-181">Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="1c75d-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="1c75d-182">Na serwerze uruchom **usługę setup.bat** w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1c75d-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="1c75d-183">Uruchomienie **pliku setup.bat** z argumentem **usługi** tworzy certyfikat usługi o w pełni kwalifikowanej nazwie domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="1c75d-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="1c75d-184">Edytuj web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), który jest taki sam jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="1c75d-185">Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1c75d-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="1c75d-186">Na kliencie uruchom **klienta setup.bat** w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1c75d-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="1c75d-187">Uruchomienie **pliku setup.bat** z argumentem **klienta** tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="1c75d-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="1c75d-188">W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="1c75d-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="1c75d-189">W tym celu można zastąpić hosta lokalnego w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="1c75d-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="1c75d-190">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="1c75d-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="1c75d-191">Na kliencie uruchom plik ImportServiceCert.bat w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="1c75d-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="1c75d-192">Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="1c75d-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="1c75d-193">Na serwerze uruchom plik ImportClientCert.bat w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="1c75d-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="1c75d-194">Spowoduje to zaimportowanie certyfikatu klienta z pliku Client.cer do magazynu LocalMachine — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="1c75d-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="1c75d-195">Na komputerze klienckim uruchom program Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1c75d-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="1c75d-196">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1c75d-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1c75d-197">Aby oczyścić po próbce</span><span class="sxs-lookup"><span data-stu-id="1c75d-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="1c75d-198">Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="1c75d-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1c75d-199">Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="1c75d-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="1c75d-200">Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="1c75d-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="1c75d-201">Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="1c75d-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
