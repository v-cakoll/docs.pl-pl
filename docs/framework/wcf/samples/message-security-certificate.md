---
title: Certyfikat zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b556cb7a0ac518957f449dd266cab6968b07e357
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041590"
---
# <a name="message-security-certificate"></a><span data-ttu-id="87e5c-102">Certyfikat zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="87e5c-102">Message Security Certificate</span></span>
<span data-ttu-id="87e5c-103">Ten przykład demonstruje sposób implementacji aplikacji, która korzysta z protokołu WS-Security przy użyciu uwierzytelniania certyfikatów X.509 v3 klienta i wymaga uwierzytelnienia serwera za pomocą certyfikat serwera X.509 v3.</span><span class="sxs-lookup"><span data-stu-id="87e5c-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="87e5c-104">Ta próbka używa domyślnych ustawień w taki sposób, że wszystkie komunikaty aplikacji między klientem i serwerem są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="87e5c-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="87e5c-105">Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) i składa się z programu konsoli klienta i Biblioteka usługi hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="87e5c-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="87e5c-106">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="87e5c-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87e5c-107">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="87e5c-108">W przykładzie pokazano kontroli uwierzytelniania przy użyciu konfiguracji i jak można uzyskać tożsamości elementu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="87e5c-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

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
  
 <span data-ttu-id="87e5c-109">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą i jeden punkt końcowy do udostępniania dokumentu WSDL usługi przy użyciu protokołu WS-MetadataExchange zdefiniowane przy użyciu pliku konfiguracji (Web.config).</span><span class="sxs-lookup"><span data-stu-id="87e5c-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="87e5c-110">Punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="87e5c-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="87e5c-111">Powiązanie jest skonfigurowane przy użyciu standardowego [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu, którego wartość domyślna to korzystanie z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="87e5c-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="87e5c-112">W tym przykładzie ustawia `clientCredentialType` atrybutów do certyfikatu, aby wymagać uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
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
  
 <span data-ttu-id="87e5c-113">Zachowanie Określa poświadczenia, które są używane, gdy klient uwierzytelnia się usługi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="87e5c-114">Nazwa podmiotu certyfikatu serwera jest określona w `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
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
  
 <span data-ttu-id="87e5c-115">Konfiguracja punktu końcowego klienta składa się z adresem bezwzględnym dla punktu końcowego usługi, powiązanie i zamówienia.</span><span class="sxs-lookup"><span data-stu-id="87e5c-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="87e5c-116">Klient powiązanie skonfigurowano tryb zabezpieczeń odpowiednich i tryb uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="87e5c-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="87e5c-117">Podczas uruchamiania w przypadku wielu komputerów, upewnij się, odpowiednio zmieniony adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
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
  
 <span data-ttu-id="87e5c-118">Implementacja klienta można ustawić certyfikatu do użycia, za pomocą pliku konfiguracji lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="87e5c-119">Poniższy przykład pokazuje, jak ustawić certyfikat do użycia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87e5c-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="87e5c-120">Poniższy przykład pokazuje sposób wywołania tej usługi w programie.</span><span class="sxs-lookup"><span data-stu-id="87e5c-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="87e5c-121">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="87e5c-122">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="87e5c-123">Plik wsadowy Setup.bat jest dołączone do przykładów zabezpieczenia komunikatów umożliwia konfigurowanie klienta i serwera przy użyciu odpowiednich certyfikatów uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="87e5c-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="87e5c-124">Plik wsadowy mogą być uruchamiane w trzech trybów.</span><span class="sxs-lookup"><span data-stu-id="87e5c-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="87e5c-125">Do uruchamiania w trybie pojedynczego komputera typu **setup.bat** w Visual Studio Command Prompt ";" dla typu tryb usługi **setup.bat usługi**; i typ trybu klienta **klienta setup.bat** .</span><span class="sxs-lookup"><span data-stu-id="87e5c-125">To run in single-computer mode type **setup.bat** in a Visual Studio Command Prompt ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="87e5c-126">Użyj trybu klienta i serwera na komputerach działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="87e5c-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="87e5c-127">Zapoznaj się z procedurą konfiguracji na końcu tego tematu, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="87e5c-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="87e5c-128">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="87e5c-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
-   <span data-ttu-id="87e5c-129">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="87e5c-130">Następujący wiersz w pliku wsadowym tworzy certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="87e5c-131">Podana nazwa klienta jest używany w nazwie podmiotu certyfikatu, utworzony.</span><span class="sxs-lookup"><span data-stu-id="87e5c-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="87e5c-132">Certyfikat jest przechowywany w `My` przechowywać `CurrentUser` lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="87e5c-133">Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="87e5c-134">Następujący wiersz w kopii pliku wsadowego certyfikat klienta do serwera TrustedPeople przechowywać tak, aby istotne zaufania lub decyzji dotyczących zaufania nie mogą być serwera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="87e5c-135">Aby uzyskać certyfikat, który został zainstalowany w magazynie TrustedPeople być uważany za zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być równa `PeerOrChainTrust` lub `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="87e5c-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="87e5c-136">Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87e5c-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   <span data-ttu-id="87e5c-137">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="87e5c-138">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="87e5c-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="87e5c-139">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="87e5c-140">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="87e5c-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="87e5c-141">Jeśli plik wsadowy Setup.bat jest uruchamiany z nieprawidłowym argumentem usługi (takie jak **usługi setup.bat**) nazwa_serwera % zawiera w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="87e5c-142">W przeciwnym razie wartość domyślna hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="87e5c-142">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="87e5c-143">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="87e5c-144">Następujący wiersz kopiuje certyfikatu serwera w magazynie zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="87e5c-145">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="87e5c-146">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="87e5c-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="87e5c-147">Przyznawanie uprawnień do klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="87e5c-148">Następujące wiersze w plik Setup.bat jest udostępnić certyfikat serwera, przechowywane w magazynie dostępne dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces roboczy.</span><span class="sxs-lookup"><span data-stu-id="87e5c-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
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
    >  <span data-ttu-id="87e5c-149">Jeśli używasz spoza USA Angielskiej wersji systemu Windows, należy edytować Setup.bat i zastąp nazwę konta "NT AUTHORITY\NETWORK SERVICE" ekwiwalent regionalne.</span><span class="sxs-lookup"><span data-stu-id="87e5c-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87e5c-150">Narzędzia używane w tym pliku wsadowego znajdują się w 8\Common7\tools C:\Program Files\Microsoft Visual Studio lub C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="87e5c-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="87e5c-151">Jeden z tych katalogów musi być w ścieżce systemowej.</span><span class="sxs-lookup"><span data-stu-id="87e5c-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="87e5c-152">Jeśli masz zainstalowany program Visual Studio, otwórz wiersz polecenia programu Visual Studio jest najprostszym sposobem, aby uzyskać ten katalog w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="87e5c-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Visual Studio Command Prompt.</span></span> <span data-ttu-id="87e5c-153">Kliknij przycisk **Start**, a następnie wybierz pozycję **wszystkie programy**, **programu Visual Studio 2012**, **narzędzia**.</span><span class="sxs-lookup"><span data-stu-id="87e5c-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="87e5c-154">Ten wiersz polecenia zawiera odpowiednie ścieżki już skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="87e5c-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="87e5c-155">W przeciwnym razie należy dodać odpowiedni katalog do ścieżki ręcznie.</span><span class="sxs-lookup"><span data-stu-id="87e5c-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87e5c-156">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="87e5c-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="87e5c-157">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="87e5c-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="87e5c-158">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="87e5c-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87e5c-159">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="87e5c-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="87e5c-160">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="87e5c-160">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="87e5c-161">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87e5c-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="87e5c-162">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87e5c-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="87e5c-163">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="87e5c-163">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="87e5c-164">Otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat jest z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="87e5c-164">Open a Visual Studio Command Prompt  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="87e5c-165">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87e5c-166">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87e5c-166">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt .</span></span> <span data-ttu-id="87e5c-167">Wymaga to, że zmiennej środowiskowej path odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="87e5c-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="87e5c-168">Ta zmienna środowiskowa jest automatycznie ustawiana w ramach wiersza polecenia Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="87e5c-168">This environment variable is automatically set within a Visual Studio Command Prompt (2010).</span></span>  
  
2.  <span data-ttu-id="87e5c-169">Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="87e5c-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3.  <span data-ttu-id="87e5c-170">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="87e5c-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="87e5c-171">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-171">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="87e5c-172">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="87e5c-172">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="87e5c-173">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="87e5c-173">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="87e5c-174">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-174">Create a directory on the service computer.</span></span> <span data-ttu-id="87e5c-175">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="87e5c-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="87e5c-176">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="87e5c-177">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="87e5c-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="87e5c-178">Także skopiować pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="87e5c-179">Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="87e5c-180">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="87e5c-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="87e5c-181">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="87e5c-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="87e5c-182">Na serwerze, uruchom **usługi setup.bat** w wierszu polecenia programu Visual Studio z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="87e5c-182">On the server, run **setup.bat service** in a Visual Studio command prompt with administrator privileges.</span></span> <span data-ttu-id="87e5c-183">Uruchamianie **setup.bat** z **usługi** argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="87e5c-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="87e5c-184">Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="87e5c-185">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="87e5c-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="87e5c-186">Na komputerze klienckim, należy uruchomić **klienta setup.bat** w wierszu polecenia programu Visual Studio z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="87e5c-186">On the client, run **setup.bat client** in a Visual Studio command prompt with administrator privileges.</span></span> <span data-ttu-id="87e5c-187">Uruchamianie **setup.bat** z **klienta** argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="87e5c-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="87e5c-188">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="87e5c-189">To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="87e5c-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="87e5c-190">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="87e5c-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="87e5c-191">Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-191">On the client, run ImportServiceCert.bat in a Visual Studio command prompt with administrative privileges.</span></span> <span data-ttu-id="87e5c-192">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="87e5c-193">Na serwerze, uruchom ImportClientCert.bat w wierszu polecenia programu Visual Studio z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="87e5c-193">On the server, run ImportClientCert.bat in a Visual Studio command prompt with administrative privileges.</span></span> <span data-ttu-id="87e5c-194">To importuje certyfikat klienta z pliku Client.cer, do maszyny lokalnej - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="87e5c-195">Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="87e5c-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="87e5c-196">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="87e5c-196">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="87e5c-197">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="87e5c-197">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="87e5c-198">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="87e5c-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87e5c-199">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="87e5c-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="87e5c-200">Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="87e5c-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="87e5c-201">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="87e5c-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e5c-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87e5c-202">See Also</span></span>
