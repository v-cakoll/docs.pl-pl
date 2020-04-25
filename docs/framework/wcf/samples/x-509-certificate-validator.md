---
title: Moduł weryfikacji certyfikatów X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: ba73381bb6211dcbd1ddad1457f9ae8611008d43
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141211"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="55b43-102">Moduł weryfikacji certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="55b43-102">X.509 Certificate Validator</span></span>

<span data-ttu-id="55b43-103">Ten przykład pokazuje, jak zaimplementować niestandardowy moduł sprawdzania poprawności certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="55b43-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="55b43-104">Jest to przydatne w przypadkach, gdy żaden z wbudowanych trybów weryfikacji certyfikatu X. 509 nie jest odpowiedni dla wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55b43-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="55b43-105">Ten przykład pokazuje usługę, która ma niestandardowy moduł sprawdzania poprawności akceptujący certyfikaty wystawione automatycznie.</span><span class="sxs-lookup"><span data-stu-id="55b43-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="55b43-106">Klient używa takiego certyfikatu do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="55b43-106">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="55b43-107">Uwaga: ponieważ każdy może utworzyć certyfikat z własnym wystawiony, niestandardowy moduł sprawdzania poprawności używany przez usługę jest mniej bezpieczny niż domyślne zachowanie udostępniane przez ChainTrust X509CertificateValidationMode.</span><span class="sxs-lookup"><span data-stu-id="55b43-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="55b43-108">Należy uważnie rozważyć implikacje zabezpieczeń przed użyciem tej logiki walidacji w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="55b43-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="55b43-109">W podsumowaniu ten przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="55b43-109">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="55b43-110">Klienta można uwierzytelnić przy użyciu certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="55b43-110">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="55b43-111">Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="55b43-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="55b43-112">Serwer jest uwierzytelniany przy użyciu certyfikatu X. 509 serwera.</span><span class="sxs-lookup"><span data-stu-id="55b43-112">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="55b43-113">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji App. config. Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="55b43-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="55b43-114">Powiązanie jest skonfigurowane ze standardem `wsHttpBinding` , który jest domyślnie używany `WSSecurity` do uwierzytelniania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="55b43-115">Zachowanie usługi określa niestandardowy tryb weryfikacji certyfikatów X. 509 klienta oraz typ klasy modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="55b43-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="55b43-116">Zachowanie określa również certyfikat serwera przy użyciu elementu serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="55b43-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="55b43-117">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jak `findValue` w [ \<>serviceCertificate ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="55b43-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="55b43-118">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="55b43-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="55b43-119">Powiązanie klienta jest skonfigurowane z odpowiednim trybem i komunikatem `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="55b43-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

<span data-ttu-id="55b43-120">Implementacja klienta ustawia używany certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-120">The client implementation sets the client certificate to use.</span></span>

```csharp
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

<span data-ttu-id="55b43-121">Ten przykład używa niestandardowego X509CertificateValidator do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="55b43-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="55b43-122">Przykład implementuje CustomX509CertificateValidator, pochodzące od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="55b43-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="55b43-123"><xref:System.IdentityModel.Selectors.X509CertificateValidator> Aby uzyskać więcej informacji, zobacz dokumentację.</span><span class="sxs-lookup"><span data-stu-id="55b43-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="55b43-124">Ten konkretny niestandardowy przykład modułu sprawdzania poprawności implementuje metodę Validate, aby akceptować dowolny certyfikat X. 509, który został wystawiony jako przedstawiony w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="55b43-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
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

 <span data-ttu-id="55b43-125">Po wdrożeniu modułu sprawdzania poprawności w kodzie usługi Host usługi musi zostać poinformowany o wystąpieniu modułu sprawdzania poprawności, które ma być używane.</span><span class="sxs-lookup"><span data-stu-id="55b43-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="55b43-126">Jest to realizowane przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="55b43-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="55b43-127">Można też wykonać tę czynność w konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="55b43-127">Or you can do the same thing in configuration as follows.</span></span>

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
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="55b43-128">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="55b43-129">Klient powinien pomyślnie wywołać wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="55b43-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="55b43-130">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="55b43-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="55b43-131">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55b43-131">Setup Batch File</span></span>

<span data-ttu-id="55b43-132">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="55b43-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="55b43-133">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="55b43-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="55b43-134">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="55b43-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="55b43-135">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="55b43-135">Creating the server certificate:</span></span>

     <span data-ttu-id="55b43-136">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="55b43-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="55b43-137">Zmienna% SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="55b43-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="55b43-138">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="55b43-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="55b43-139">Wartość domyślna to localhost.</span><span class="sxs-lookup"><span data-stu-id="55b43-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="55b43-140">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="55b43-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="55b43-141">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="55b43-142">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="55b43-143">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="55b43-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="55b43-144">Tworzenie certyfikatu klienta:</span><span class="sxs-lookup"><span data-stu-id="55b43-144">Creating the client certificate:</span></span>

     <span data-ttu-id="55b43-145">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="55b43-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="55b43-146">Zmienna% USER_NAME% określa nazwę klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="55b43-147">Ta wartość jest ustawiona na "test1", ponieważ jest to nazwa, której szuka kod klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="55b43-148">W przypadku zmiany wartości% USER_NAME% należy zmienić odpowiadającą jej wartość w pliku źródłowym Client.cs i skompilować ponownie klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="55b43-149">Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="55b43-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="55b43-150">Instalowanie certyfikatu klienta w zaufanym magazynie certyfikatów serwera:</span><span class="sxs-lookup"><span data-stu-id="55b43-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="55b43-151">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat klienta do magazynu osób zaufanych.</span><span class="sxs-lookup"><span data-stu-id="55b43-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="55b43-152">Ten krok jest wymagany, ponieważ system serwera nie ufa certyfikatom wygenerowanym przez Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="55b43-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="55b43-153">Jeśli masz już certyfikat, który został odblokowany w zaufanym certyfikacie głównym — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów serwera z certyfikatem klienta nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="55b43-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="55b43-154">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="55b43-154">To set up and build the sample</span></span>

1. <span data-ttu-id="55b43-155">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55b43-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="55b43-156">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.</span><span class="sxs-lookup"><span data-stu-id="55b43-156">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="55b43-157">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="55b43-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="55b43-158">Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 otwartym z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="55b43-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="55b43-159">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="55b43-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="55b43-160">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="55b43-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="55b43-161">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="55b43-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="55b43-162">Uruchom usługę Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="55b43-162">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="55b43-163">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="55b43-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="55b43-164">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="55b43-165">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="55b43-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="55b43-166">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="55b43-166">To run the sample across computers</span></span>

1. <span data-ttu-id="55b43-167">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="55b43-167">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="55b43-168">Skopiuj pliki programu usługi z \service\bin do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="55b43-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="55b43-169">Skopiuj także pliki Setup. bat, Oczyść. bat, getcomputers. vbs i ImportClientCert. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="55b43-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="55b43-170">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="55b43-170">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="55b43-171">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="55b43-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="55b43-172">Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="55b43-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="55b43-173">Na serwerze programu uruchom `setup.bat service` polecenie w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="55b43-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="55b43-174">Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.</span><span class="sxs-lookup"><span data-stu-id="55b43-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="55b43-175">Edytuj plik Service. exe. config, aby odzwierciedlić nową nazwę certyfikatu ( `findValue` w atrybucie w [ \<>serviceCertificate ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="55b43-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="55b43-176">Zmień również nazwę komputera w ramach \<usługi>/\<baseAddresses> z localhost na w pełni kwalifikowaną nazwę komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="55b43-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="55b43-177">Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="55b43-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="55b43-178">Na kliencie Uruchom `setup.bat client` program w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="55b43-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="55b43-179">Uruchomienie `setup.bat` z `client` argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.</span><span class="sxs-lookup"><span data-stu-id="55b43-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="55b43-180">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="55b43-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="55b43-181">Aby to zrobić, Zastąp wartość localhost nazwą FQDN serwera.</span><span class="sxs-lookup"><span data-stu-id="55b43-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="55b43-182">Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="55b43-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="55b43-183">Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="55b43-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="55b43-184">Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="55b43-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="55b43-185">Na serwerze programu Uruchom program ImportClientCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="55b43-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="55b43-186">Spowoduje to zaimportowanie certyfikatu klienta z pliku. cer klienta do magazynu LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="55b43-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="55b43-187">Na komputerze serwera Uruchom polecenie Service. exe w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="55b43-187">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="55b43-188">Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="55b43-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="55b43-189">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="55b43-189">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="55b43-190">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="55b43-190">To clean up after the sample</span></span>

1. <span data-ttu-id="55b43-191">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="55b43-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="55b43-192">Spowoduje to usunięcie certyfikatów serwera i klienta z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="55b43-192">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="55b43-193">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami.</span><span class="sxs-lookup"><span data-stu-id="55b43-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="55b43-194">W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="55b43-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="55b43-195">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład:. `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="55b43-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
