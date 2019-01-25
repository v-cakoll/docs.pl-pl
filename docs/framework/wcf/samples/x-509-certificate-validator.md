---
title: Moduł weryfikacji certyfikatów X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 8c87e1d8c84af500e1f415b79e7f3ec006b51860
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510133"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="9990e-102">Moduł weryfikacji certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="9990e-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="9990e-103">Niniejszy przykład pokazuje, jak zaimplementować niestandardowy moduł weryfikacji certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="9990e-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="9990e-104">Jest to przydatne w przypadkach, gdy żadna z wbudowanych metod walidacji certyfikatu X.509 jest odpowiednia dla wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9990e-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="9990e-105">Niniejszy przykład pokazuje usługi, która ma niestandardowy moduł sprawdzania poprawności, który akceptuje własnym wystawionych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9990e-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="9990e-106">Klient używa takiego certyfikatu do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="9990e-106">The client uses such a certificate to authenticate to the service.</span></span>

 <span data-ttu-id="9990e-107">Uwaga: Niestandardowy moduł sprawdzania poprawności, używane przez usługę jest mniej bezpieczna niż zachowanie domyślne, dostarczone przez ChainTrust X509CertificateValidationMode, jak każdy może utworzyć własny wystawionego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="9990e-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="9990e-108">Ryzyko związane z tym powinien zostać starannie przemyślany, przed użyciem tej logiki weryfikacji w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="9990e-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

 <span data-ttu-id="9990e-109">W podsumowaniu Niniejszy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="9990e-109">In summary this sample demonstrates how:</span></span>

-   <span data-ttu-id="9990e-110">Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="9990e-110">The client can be authenticated using an X.509 certificate.</span></span>

-   <span data-ttu-id="9990e-111">Serwer sprawdza poprawność poświadczeń klienta względem X509CertificateValidator niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9990e-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

-   <span data-ttu-id="9990e-112">Serwer jest uwierzytelniany przy użyciu certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="9990e-112">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="9990e-113">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9990e-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="9990e-114">Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` , domyślnie używane są `WSSecurity` i uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="9990e-115">Zachowanie usługi Określa tryb niestandardowego sprawdzania poprawności certyfikatów X.509 klienta wraz z typu klasy modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="9990e-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="9990e-116">Zachowanie określa również certyfikat serwera za pomocą elementu serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="9990e-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="9990e-117">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="9990e-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="9990e-118">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia.</span><span class="sxs-lookup"><span data-stu-id="9990e-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="9990e-119">Klient powiązanie skonfigurowano odpowiedni tryb i wiadomości `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="9990e-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="9990e-120">Implementacja klienta ustawia certyfikat klienta do użycia.</span><span class="sxs-lookup"><span data-stu-id="9990e-120">The client implementation sets the client certificate to use.</span></span>

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

 <span data-ttu-id="9990e-121">Ta próbka używa niestandardowych X509CertificateValidator do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9990e-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="9990e-122">Przykład implementuje CustomX509CertificateValidator, pochodzące z <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="9990e-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="9990e-123">Zobacz dokumentację na temat <xref:System.IdentityModel.Selectors.X509CertificateValidator> Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="9990e-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="9990e-124">W tym przykładzie niestandardowego modułu sprawdzania poprawności implementuje metodę sprawdzania poprawności, aby zaakceptować certyfikat X.509, wszelkie własnym wystawiony, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9990e-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

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

 <span data-ttu-id="9990e-125">Po wdrożeniu modułu sprawdzania poprawności jest w kodzie usługi hosta usługi muszą zostać powiadomieni o wystąpieniu weryfikacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="9990e-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="9990e-126">Odbywa się przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="9990e-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="9990e-127">Lub można zrobić to samo w konfiguracji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="9990e-127">Or you can do the same thing in configuration as follows.</span></span>

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
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="9990e-128">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9990e-129">Klient pomyślnie należy wywołać wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="9990e-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="9990e-130">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="9990e-131">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="9990e-131">Setup Batch File</span></span>
 <span data-ttu-id="9990e-132">Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia aplikacji własnego wymagającego zabezpieczenia oparte na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="9990e-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="9990e-133">Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="9990e-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="9990e-134">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="9990e-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

-   <span data-ttu-id="9990e-135">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="9990e-135">Creating the server certificate:</span></span>

     <span data-ttu-id="9990e-136">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9990e-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="9990e-137">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="9990e-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9990e-138">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="9990e-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="9990e-139">Wartość domyślna to hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="9990e-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="9990e-140">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="9990e-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="9990e-141">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="9990e-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="9990e-142">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9990e-143">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="9990e-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="9990e-144">Tworzenie certyfikatu klienta:</span><span class="sxs-lookup"><span data-stu-id="9990e-144">Creating the client certificate:</span></span>

     <span data-ttu-id="9990e-145">Następujące wiersze z pliku wsadowego Setup.bat utworzenia certyfikatu klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9990e-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="9990e-146">% Zmienna % nazwa_użytkownika Określa nazwę klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="9990e-147">Ta wartość jest równa "test1", ponieważ jest to nazwa, którą wyszukuje kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="9990e-148">Jeśli zmienisz wartość % nazwa_użytkownika należy zmienić odpowiednie wartości w pliku źródłowym Client.cs i ponownie skompilować klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="9990e-149">Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="9990e-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="9990e-150">Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera:</span><span class="sxs-lookup"><span data-stu-id="9990e-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="9990e-151">Następujące wiersze w pliku wsadowym Setup.bat skopiuj certyfikat klienta do magazynu osób zaufanych.</span><span class="sxs-lookup"><span data-stu-id="9990e-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="9990e-152">Ten krok jest wymagany, ponieważ certyfikaty generowaną przez Makecert.exe nie niejawnie cieszą się zaufaniem systemu serwera.</span><span class="sxs-lookup"><span data-stu-id="9990e-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="9990e-153">Jeśli masz już certyfikat, który jest ścieżką w zaufany certyfikat główny — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów serwera za pomocą certyfikatu klienta nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="9990e-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9990e-154">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="9990e-154">To set up and build the sample</span></span>

1.  <span data-ttu-id="9990e-155">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9990e-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2.  <span data-ttu-id="9990e-156">Do uruchomienia przykładu w jednym — lub cross-computerconfiguration, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9990e-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9990e-157">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="9990e-157">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="9990e-158">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia programu Visual Studio 2012 otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9990e-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="9990e-159">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="9990e-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="9990e-160">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="9990e-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="9990e-161">Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="9990e-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="9990e-162">Uruchom Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="9990e-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="9990e-163">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="9990e-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="9990e-164">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="9990e-165">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9990e-165">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9990e-166">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="9990e-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="9990e-167">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="9990e-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="9990e-168">Skopiuj pliki programu usługi z \service\bin do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="9990e-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="9990e-169">Także skopiować pliki Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat, aby komputer z usługą.</span><span class="sxs-lookup"><span data-stu-id="9990e-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="9990e-170">Utwórz katalog na computerfor klienta plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="9990e-171">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="9990e-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="9990e-172">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="9990e-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="9990e-173">Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9990e-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="9990e-174">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny wywozu computerand certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="9990e-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="9990e-175">Edytuj Service.exe.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="9990e-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="9990e-176">Również zmienić nazwę komputera w \<usługi > /\<baseAddresses > element z hostem lokalnym do w pełni kwalifikowanej nazwy komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="9990e-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="9990e-177">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="9990e-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="9990e-178">Na komputerze klienckim, należy uruchomić `setup.bat client` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9990e-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="9990e-179">Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="9990e-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="9990e-180">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="9990e-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="9990e-181">To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="9990e-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="9990e-182">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="9990e-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="9990e-183">Na komputerze klienckim uruchom ImportServiceCert.bat w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9990e-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="9990e-184">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="9990e-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="9990e-185">Na serwerze uruchom ImportClientCert.bat w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9990e-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="9990e-186">To importuje certyfikat klienta z pliku Client.cer, do maszyny lokalnej - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="9990e-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="9990e-187">Na komputerze serwera uruchomić Service.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9990e-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="9990e-188">Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9990e-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="9990e-189">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9990e-189">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9990e-190">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="9990e-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="9990e-191">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="9990e-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="9990e-192">Spowoduje to usunięcie certyfikaty klienta i serwera z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9990e-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9990e-193">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="9990e-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="9990e-194">Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="9990e-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="9990e-195">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="9990e-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9990e-196">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9990e-196">See also</span></span>
