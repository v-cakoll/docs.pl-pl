---
title: "Moduł weryfikacji certyfikatów X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08ccbbf50db089841d2af2205c7a7cb289a8767c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="2fcac-102">Moduł weryfikacji certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="2fcac-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="2fcac-103">W tym przykładzie pokazano, jak do zaimplementowania niestandardowego modułu weryfikacji certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="2fcac-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="2fcac-104">Jest to przydatne w sytuacjach, gdy żaden z wbudowanych tryby walidacji certyfikatu X.509 nie jest odpowiednią do wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2fcac-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="2fcac-105">W tym przykładzie pokazano usługi, która ma niestandardowego modułu weryfikacji akceptuje własnym wystawionych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2fcac-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="2fcac-106">Klient używa takiego certyfikatu do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2fcac-106">The client uses such a certificate to authenticate to the service.</span></span>  
  
 <span data-ttu-id="2fcac-107">Uwaga: ponieważ każda osoba, która może utworzyć certyfikat wystawiony samodzielnie niestandardowego modułu weryfikacji, używane przez usługę jest mniej bezpieczna niż udostępniane przez ChainTrust X509CertificateValidationMode zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="2fcac-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="2fcac-108">Ryzyko związane z tym powinien zostać starannie przemyślany, przed użyciem tej logiki sprawdzania poprawności w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2fcac-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>  
  
 <span data-ttu-id="2fcac-109">W podsumowaniu przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="2fcac-109">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="2fcac-110">Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2fcac-110">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="2fcac-111">Serwer sprawdza poprawność poświadczeń klienta przed niestandardowego obiektu X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="2fcac-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>  
  
-   <span data-ttu-id="2fcac-112">Serwer jest uwierzytelniany przy użyciu certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="2fcac-112">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="2fcac-113">Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2fcac-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2fcac-114">Powiązanie jest skonfigurowane z normą `wsHttpBinding` który używa domyślnie `WSSecurity` i uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="2fcac-115">Zachowanie usługi Określa tryb niestandardowego sprawdzania poprawności certyfikatów X.509 klienta wraz z typem klasy modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="2fcac-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="2fcac-116">Zachowanie określa również za pomocą elementu serviceCertificate certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="2fcac-117">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="2fcac-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 <span data-ttu-id="2fcac-118">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="2fcac-119">Klient powiązanie jest skonfigurowane przy użyciu odpowiedni tryb i komunikat `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="2fcac-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="2fcac-120">Implementacja klienta ustawia certyfikat klienta do użycia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-120">The client implementation sets the client certificate to use.</span></span>  
  
```  
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="2fcac-121">W przykładzie użyto niestandardowego obiektu X509CertificateValidator, aby zweryfikować certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="2fcac-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="2fcac-122">Próbka implementuje CustomX509CertificateValidator pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="2fcac-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="2fcac-123">Zobacz dokumentację <xref:System.IdentityModel.Selectors.X509CertificateValidator> Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="2fcac-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="2fcac-124">W tym przykładzie niestandardowego modułu sprawdzania poprawności implementuje metodę sprawdzania poprawności do akceptowania dowolny certyfikat X.509 własnym wystawiony zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="2fcac-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>  
  
```  
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 <span data-ttu-id="2fcac-125">Po zaimplementowaniu w kodzie usługi modułu sprawdzania poprawności hosta usługi musi informację o wystąpienia modułu sprawdzania poprawności do użycia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="2fcac-126">Jest to realizowane przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-126">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 <span data-ttu-id="2fcac-127">Lub tak samo postąpić w konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="2fcac-127">Or you can do the same thing in configuration as follows.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="2fcac-128">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2fcac-129">Klient pomyślnie powinny wywoływać wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="2fcac-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="2fcac-130">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-130">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="2fcac-131">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="2fcac-131">Setup Batch File</span></span>  
 <span data-ttu-id="2fcac-132">Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="2fcac-133">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="2fcac-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="2fcac-134">Poniżej przedstawiono krótkie omówienie różne sekcje pliki wsadowe, tak, aby można modyfikować w prawidłowej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="2fcac-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="2fcac-135">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="2fcac-135">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="2fcac-136">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="2fcac-137">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2fcac-138">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2fcac-139">Wartość domyślna to localhost.</span><span class="sxs-lookup"><span data-stu-id="2fcac-139">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="2fcac-140">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="2fcac-140">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="2fcac-141">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2fcac-142">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2fcac-143">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="2fcac-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="2fcac-144">Tworzenie certyfikatu klienta:</span><span class="sxs-lookup"><span data-stu-id="2fcac-144">Creating the client certificate:</span></span>  
  
     <span data-ttu-id="2fcac-145">Następujące wiersze z pliku wsadowego pliku Setup.bat Utwórz certyfikat klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2fcac-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="2fcac-146">% Zmienna % nazwa_użytkownika Określa nazwę klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="2fcac-147">Ta wartość jest równa "test1", ponieważ jest to nazwa, które wyszukuje kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="2fcac-148">W przypadku zmiany wartości nazwa_użytkownika % należy zmienić odpowiednie wartości w pliku źródłowym Client.cs i skompiluj ponownie klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>  
  
     <span data-ttu-id="2fcac-149">Certyfikat jest przechowywany w magazynie My (osobistych) w lokalizacji w magazynie CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="2fcac-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="2fcac-150">Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera:</span><span class="sxs-lookup"><span data-stu-id="2fcac-150">Installing the client certificate into server's trusted certificate store:</span></span>  
  
     <span data-ttu-id="2fcac-151">Następujące wiersze w pliku wsadowym pliku Setup.bat skopiuj certyfikat klienta w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="2fcac-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="2fcac-152">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu serwera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="2fcac-153">Jeśli masz już certyfikatu, który jest ścieżką do katalogu głównego w zaufanym certyfikatem głównym — na przykład certyfikat wystawiony Microsoft — ten krok zapełnianie magazynu certyfikatów na serwerze przy użyciu certyfikatu klienta nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="2fcac-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2fcac-154">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="2fcac-154">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="2fcac-155">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fcac-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="2fcac-156">Aby uruchomić przykład w jednym - lub cross-computerconfiguration, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2fcac-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2fcac-157">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="2fcac-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="2fcac-158">Uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2fcac-158">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="2fcac-159">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2fcac-160">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="2fcac-161">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="2fcac-162">Uruchom Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="2fcac-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="2fcac-163">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2fcac-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2fcac-164">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="2fcac-165">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2fcac-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2fcac-166">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="2fcac-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="2fcac-167">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="2fcac-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="2fcac-168">Skopiuj pliki programu usługi z \service\bin do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="2fcac-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="2fcac-169">Także skopiować pliki pliku Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="2fcac-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="2fcac-170">Utwórz katalog na computerfor klienta pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="2fcac-171">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2fcac-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2fcac-172">Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="2fcac-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="2fcac-173">Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2fcac-173">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="2fcac-174">Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę eksportu computerand certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="2fcac-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="2fcac-175">Edytuj Service.exe.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="2fcac-176">Również zmienić nazwę komputera w \<usługi > /\<baseAddresses > element na podstawie localhost pełną nazwę komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="2fcac-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="2fcac-177">Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2fcac-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="2fcac-178">Na komputerze klienckim, uruchom `setup.bat client` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2fcac-178">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="2fcac-179">Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="2fcac-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="2fcac-180">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="2fcac-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="2fcac-181">W tym celu zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="2fcac-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="2fcac-182">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2fcac-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="2fcac-183">Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2fcac-183">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="2fcac-184">Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="2fcac-185">Na serwerze należy uruchomić ImportClientCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2fcac-185">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="2fcac-186">Certyfikat klienta to importuje z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="2fcac-187">Na komputerze serwera Uruchom Service.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="2fcac-188">Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2fcac-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="2fcac-189">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2fcac-189">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2fcac-190">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="2fcac-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="2fcac-191">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="2fcac-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="2fcac-192">Spowoduje to usunięcie certyfikaty serwera i klienta z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2fcac-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fcac-193">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2fcac-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2fcac-194">Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="2fcac-194">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2fcac-195">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2fcac-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fcac-196">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fcac-196">See Also</span></span>
