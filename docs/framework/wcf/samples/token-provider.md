---
title: Dostawca tokenów
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: e1520ef3e2faca88b06cc82ef5ab3035a857314a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969369"
---
# <a name="token-provider"></a><span data-ttu-id="345ae-102">Dostawca tokenów</span><span class="sxs-lookup"><span data-stu-id="345ae-102">Token Provider</span></span>
<span data-ttu-id="345ae-103">Ten przykład pokazuje, jak zaimplementować niestandardowego dostawcę tokenów.</span><span class="sxs-lookup"><span data-stu-id="345ae-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="345ae-104">Dostawca tokenu w Windows Communication Foundation (WCF) służy do dostarczania poświadczeń do infrastruktury zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="345ae-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="345ae-105">Dostawca tokenu ogólnie bada cel i wystawia odpowiednie poświadczenia, aby infrastruktura zabezpieczeń mogła zabezpieczyć komunikat.</span><span class="sxs-lookup"><span data-stu-id="345ae-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="345ae-106">Usługa WCF jest dostarczana z domyślnym dostawcą tokenu Menedżera poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="345ae-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="345ae-107">Usługa WCF jest również dostarczana z dostawcą tokenu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="345ae-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="345ae-108">Dostawcy tokenów niestandardowych są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="345ae-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="345ae-109">Jeśli masz magazyn poświadczeń, którego nie mogą używać dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="345ae-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="345ae-110">Jeśli chcesz zapewnić własny niestandardowy mechanizm przekształcania poświadczeń z punktu, gdy użytkownik poda szczegółowe informacje o tym, kiedy struktura klienta programu WCF używa tych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="345ae-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="345ae-111">W przypadku kompilowania niestandardowego tokenu.</span><span class="sxs-lookup"><span data-stu-id="345ae-111">If you are building a custom token.</span></span>

 <span data-ttu-id="345ae-112">Ten przykład pokazuje, jak utworzyć niestandardowego dostawcę tokenów, który przekształca dane wejściowe użytkownika w inny format.</span><span class="sxs-lookup"><span data-stu-id="345ae-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="345ae-113">Podsumowując, ten przykład ilustruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="345ae-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="345ae-114">Jak klient może uwierzytelniać za pomocą pary username/Password.</span><span class="sxs-lookup"><span data-stu-id="345ae-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="345ae-115">Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="345ae-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="345ae-116">Sposób, w jaki serwer może sprawdzać poprawność poświadczeń klienta przy <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> użyciu hasła z niestandardowym, które sprawdza, czy nazwa użytkownika i hasło są zgodne.</span><span class="sxs-lookup"><span data-stu-id="345ae-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="345ae-117">Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X. 509 serwera.</span><span class="sxs-lookup"><span data-stu-id="345ae-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="345ae-118">Ten przykład pokazuje również, jak tożsamość wywołującego jest dostępna po procesie uwierzytelniania tokenu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="345ae-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="345ae-119">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji App. config.</span><span class="sxs-lookup"><span data-stu-id="345ae-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="345ae-120">Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="345ae-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="345ae-121">Powiązanie jest skonfigurowane przy użyciu standardu `wsHttpBinding`, który domyślnie używa zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="345ae-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="345ae-122">Ten przykład ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="345ae-123">Usługa konfiguruje również certyfikat usługi przy użyciu zachowania ServiceCredentials.</span><span class="sxs-lookup"><span data-stu-id="345ae-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="345ae-124">Zachowanie serviceCredentials służy do konfigurowania certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="345ae-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="345ae-125">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewniania ochrony komunikatów.</span><span class="sxs-lookup"><span data-stu-id="345ae-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="345ae-126">Następująca konfiguracja odwołuje się do certyfikatu localhost zainstalowanego podczas konfiguracji przykładowej zgodnie z opisem w poniższych instrukcjach dotyczących instalacji.</span><span class="sxs-lookup"><span data-stu-id="345ae-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
        The serviceCredentials behavior allows one to define a service certificate.
        A service certificate is used by a client to authenticate the service and provide message protection.
        This configuration references the "localhost" certificate installed during the setup instructions.
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="345ae-127">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="345ae-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="345ae-128">Powiązanie klienta jest skonfigurowane z odpowiednim `Mode` komunikatem `clientCredentialType`i.</span><span class="sxs-lookup"><span data-stu-id="345ae-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
              address="http://localhost:8000/servicemodelsamples/service"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator">
    </endpoint>
  </client>

  <bindings>
    <wsHttpBinding>
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
</system.serviceModel>
```

 <span data-ttu-id="345ae-129">Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenów i zintegrować go z platformą zabezpieczeń WCF:</span><span class="sxs-lookup"><span data-stu-id="345ae-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="345ae-130">Napisz niestandardowego dostawcę tokenów.</span><span class="sxs-lookup"><span data-stu-id="345ae-130">Write a custom token provider.</span></span>

     <span data-ttu-id="345ae-131">Przykład implementuje niestandardowego dostawcę tokenów, który uzyskuje nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="345ae-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="345ae-132">Hasło musi być zgodne z tą nazwą użytkownika.</span><span class="sxs-lookup"><span data-stu-id="345ae-132">The password must match this username.</span></span> <span data-ttu-id="345ae-133">Ten niestandardowy dostawca tokenów służy tylko do celów demonstracyjnych i nie jest zalecany w przypadku rzeczywistego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="345ae-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="345ae-134">Aby wykonać to zadanie, dostawca niestandardowego tokenu dziedziczy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasę i <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> zastępuje metodę.</span><span class="sxs-lookup"><span data-stu-id="345ae-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="345ae-135">Ta metoda tworzy i zwraca nowy `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="345ae-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. <span data-ttu-id="345ae-136">Napisz niestandardowego menedżera tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="345ae-136">Write custom security token manager.</span></span>

     <span data-ttu-id="345ae-137">Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , które są przesyłane do niego w `CreateSecurityTokenProvider` metodzie. <xref:System.IdentityModel.Selectors.SecurityTokenManager></span><span class="sxs-lookup"><span data-stu-id="345ae-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="345ae-138">Menedżer tokenów zabezpieczających jest również używany do tworzenia wystawców tokenów i serializatorów tokenów, ale te nie są objęte tym przykładem.</span><span class="sxs-lookup"><span data-stu-id="345ae-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="345ae-139">W tym przykładzie niestandardowy Menedżer tokenów zabezpieczających dziedziczy z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i `CreateSecurityTokenProvider` przesłania metodę w celu zwrócenia niestandardowego dostawcy tokenów username, gdy spełnione wymagania dotyczące tokenu wskazują, że zażądano dostawcy nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="345ae-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. <span data-ttu-id="345ae-140">Napisz niestandardowe poświadczenie klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-140">Write a custom client credential.</span></span>

     <span data-ttu-id="345ae-141">Klasa poświadczeń klienta służy do reprezentowania poświadczeń skonfigurowanych dla serwera proxy klienta i tworzy Menedżera tokenów zabezpieczeń, który jest używany do uzyskiwania wystawców tokenów, dostawców tokenów i serializatorów tokenów.</span><span class="sxs-lookup"><span data-stu-id="345ae-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. <span data-ttu-id="345ae-142">Skonfiguruj klienta tak, aby korzystał z niestandardowego poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="345ae-143">Aby klient korzystał z niestandardowego poświadczenia klienta, przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="345ae-144">Aby wyświetlić informacje o wywołującym w usłudze, użyj <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> , jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="345ae-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="345ae-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera informacje o oświadczeniach dotyczących bieżącego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="345ae-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="345ae-146">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="345ae-147">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="345ae-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="345ae-148">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="345ae-148">Setup Batch File</span></span>
 <span data-ttu-id="345ae-149">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednim certyfikatem w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="345ae-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="345ae-150">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="345ae-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="345ae-151">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="345ae-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="345ae-152">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="345ae-152">Creating the server certificate.</span></span>

     <span data-ttu-id="345ae-153">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="345ae-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="345ae-154">`%SERVER_NAME%` Zmienna określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="345ae-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="345ae-155">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="345ae-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="345ae-156">Wartość domyślna w tym pliku wsadowym to localhost.</span><span class="sxs-lookup"><span data-stu-id="345ae-156">The default value in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="345ae-157">Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="345ae-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="345ae-158">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="345ae-159">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="345ae-160">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="345ae-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="345ae-161">Plik wsadowy Setup. bat został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="345ae-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="345ae-162">Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="345ae-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="345ae-163">Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="345ae-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="345ae-164">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="345ae-164">To set up and build the sample</span></span>

1. <span data-ttu-id="345ae-165">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="345ae-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="345ae-166">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="345ae-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="345ae-167">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="345ae-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="345ae-168">Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 otwartym z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="345ae-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="345ae-169">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="345ae-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="345ae-170">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="345ae-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="345ae-171">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="345ae-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="345ae-172">Uruchom usługę Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="345ae-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="345ae-173">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="345ae-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="345ae-174">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="345ae-175">W wierszu polecenia wpisz nazwę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="345ae-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="345ae-176">W monicie o hasło Użyj tego samego ciągu, który został wpisanych dla monitu o podanie nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="345ae-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="345ae-177">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="345ae-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="345ae-178">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="345ae-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="345ae-179">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="345ae-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="345ae-180">Skopiuj pliki programu Service Files do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="345ae-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="345ae-181">Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="345ae-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="345ae-182">Musisz mieć certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="345ae-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="345ae-183">Plik Service. exe. config musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="345ae-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="345ae-184">Można utworzyć certyfikat serwera, modyfikując plik wsadowy Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="345ae-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="345ae-185">Należy pamiętać, że plik Setup. bat musi być uruchamiany z wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="345ae-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="345ae-186">Należy ustawić `%SERVER_NAME%` zmienną na w pełni kwalifikowaną nazwę hosta komputera, który jest używany do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="345ae-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="345ae-187">Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="345ae-188">Nie trzeba tego robić, gdy certyfikat serwera zostanie wystawiony przez zaufanego wystawcy klienta.</span><span class="sxs-lookup"><span data-stu-id="345ae-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="345ae-189">W pliku Service. exe. config na komputerze usługi Zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="345ae-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="345ae-190">Na komputerze usługi Uruchom program Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="345ae-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="345ae-191">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="345ae-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="345ae-192">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="345ae-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="345ae-193">Na komputerze klienckim uruchom `Client.exe` polecenie w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="345ae-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="345ae-194">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="345ae-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="345ae-195">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="345ae-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="345ae-196">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="345ae-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
