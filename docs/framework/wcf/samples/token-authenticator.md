---
title: Wystawca uwierzytelnienia tokenów
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: f4b49edd3b5a2cecd203feed713c7694450f7497
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596555"
---
# <a name="token-authenticator"></a><span data-ttu-id="4fad0-102">Wystawca uwierzytelnienia tokenów</span><span class="sxs-lookup"><span data-stu-id="4fad0-102">Token Authenticator</span></span>
<span data-ttu-id="4fad0-103">Ten przykład pokazuje, jak zaimplementować niestandardowy wystawca uwierzytelnienia tokenów.</span><span class="sxs-lookup"><span data-stu-id="4fad0-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="4fad0-104">Wystawca uwierzytelnienia w programie Windows Communication Foundation (WCF) służy do sprawdzania poprawności tokenu użytego w komunikacie, weryfikowania, czy jest on spójny, i uwierzytelniania tożsamości skojarzonej z tokenem.</span><span class="sxs-lookup"><span data-stu-id="4fad0-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="4fad0-105">Niestandardowe wystawcy tokenów są przydatne w różnych przypadkach, takich jak:</span><span class="sxs-lookup"><span data-stu-id="4fad0-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="4fad0-106">Jeśli chcesz zastąpić domyślny mechanizm uwierzytelniania skojarzony z tokenem.</span><span class="sxs-lookup"><span data-stu-id="4fad0-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="4fad0-107">Podczas kompilowania niestandardowego tokenu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-107">When you are building a custom token.</span></span>

 <span data-ttu-id="4fad0-108">W tym przykładzie przedstawiono następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="4fad0-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="4fad0-109">Jak klient może uwierzytelniać za pomocą pary username/Password.</span><span class="sxs-lookup"><span data-stu-id="4fad0-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="4fad0-110">Jak serwer może sprawdzać poprawność poświadczeń klienta przy użyciu niestandardowego wystawcy uwierzytelnienia tokenu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="4fad0-111">Sposób powiązania kodu usługi WCF z niestandardowym wystawcą uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="4fad0-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="4fad0-112">Jak można uwierzytelniać serwer przy użyciu certyfikatu X. 509 serwera.</span><span class="sxs-lookup"><span data-stu-id="4fad0-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="4fad0-113">Ten przykład pokazuje również, jak tożsamość wywołującego jest dostępna z programu WCF po procesie uwierzytelniania tokenu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="4fad0-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="4fad0-114">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji App. config.</span><span class="sxs-lookup"><span data-stu-id="4fad0-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="4fad0-115">Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4fad0-116">Powiązanie jest skonfigurowane ze standardem `wsHttpBinding` , z trybem zabezpieczeń ustawionym na komunikat — domyślny tryb `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="4fad0-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="4fad0-117">Ten przykład ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="4fad0-118">Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowania.</span><span class="sxs-lookup"><span data-stu-id="4fad0-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="4fad0-119">`securityCredentials`Zachowanie pozwala określić certyfikat usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="4fad0-120">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewniania ochrony komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4fad0-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="4fad0-121">Następująca konfiguracja odwołuje się do certyfikatu localhost zainstalowanego podczas konfiguracji przykładowej zgodnie z opisem w poniższych instrukcjach dotyczących instalacji.</span><span class="sxs-lookup"><span data-stu-id="4fad0-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
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
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="4fad0-122">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="4fad0-123">Powiązanie klienta jest skonfigurowane z odpowiednimi `Mode` i `clientCredentialType` .</span><span class="sxs-lookup"><span data-stu-id="4fad0-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

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

 <span data-ttu-id="4fad0-124">Implementacja klienta ustawia nazwę użytkownika i hasło, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="4fad0-124">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="4fad0-125">Niestandardowe wystawcy uwierzytelniania tokenów</span><span class="sxs-lookup"><span data-stu-id="4fad0-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="4fad0-126">Aby utworzyć niestandardowy wystawca uwierzytelnienia tokenów, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4fad0-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="4fad0-127">Napisz niestandardowy wystawca uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="4fad0-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="4fad0-128">Przykład implementuje niestandardowy wystawca uwierzytelnienia tokenów, który sprawdza, czy nazwa użytkownika ma prawidłowy format wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="4fad0-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="4fad0-129">Dziedziczy <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="4fad0-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="4fad0-130">Najważniejszym sposobem w tej klasie jest <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="4fad0-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="4fad0-131">W tej metodzie wystawca uwierzytelnienia weryfikuje format nazwy użytkownika, a także że nazwa hosta nie pochodzi z nieautoryzowanej domeny.</span><span class="sxs-lookup"><span data-stu-id="4fad0-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="4fad0-132">W przypadku spełnienia obu warunków funkcja zwraca kolekcję wystąpień tylko do odczytu, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> która jest używana do dostarczania oświadczeń, które reprezentują informacje przechowywane wewnątrz tokenu username.</span><span class="sxs-lookup"><span data-stu-id="4fad0-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="4fad0-133">Podaj zasady autoryzacji, które są zwracane przez niestandardowy wystawca uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="4fad0-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="4fad0-134">Ten przykład zawiera własną implementację o <xref:System.IdentityModel.Policy.IAuthorizationPolicy> nazwie `UnconditionalPolicy` , która zwraca zestaw oświadczeń i tożsamości, które zostały do niego przesłane w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="4fad0-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="4fad0-135">Napisz niestandardowego menedżera tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4fad0-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="4fad0-136">Służy <xref:System.IdentityModel.Selectors.SecurityTokenManager> do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> dla określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> obiektów, które są do niego przenoszone w `CreateSecurityTokenAuthenticator` metodzie.</span><span class="sxs-lookup"><span data-stu-id="4fad0-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="4fad0-137">Menedżer tokenów zabezpieczających jest również używany do tworzenia dostawców tokenów i serializatorów tokenów, ale nie są one objęte tym przykładem.</span><span class="sxs-lookup"><span data-stu-id="4fad0-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="4fad0-138">W tym przykładzie niestandardowy Menedżer tokenów zabezpieczających dziedziczy z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy i przesłania `CreateSecurityTokenAuthenticator` metodę w celu zwrócenia niestandardowej wystawcy tokenów username, gdy spełnione wymagania dotyczące tokenu wskazują, że żądanie uwierzytelnienia nazwy użytkownika jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="4fad0-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="4fad0-139">Napisz niestandardowe poświadczenie usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-139">Write a custom service credential.</span></span>

     <span data-ttu-id="4fad0-140">Klasa poświadczeń usługi służy do reprezentowania poświadczeń skonfigurowanych dla usługi i tworzy Menedżera tokenów zabezpieczających, który jest używany do uzyskiwania wystawców tokenów, dostawców tokenów i serializatorów tokenów.</span><span class="sxs-lookup"><span data-stu-id="4fad0-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="4fad0-141">Skonfiguruj usługę tak, aby korzystała z poświadczeń usługi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="4fad0-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="4fad0-142">Aby usługa mogła korzystać z poświadczeń usługi niestandardowej, należy usunąć domyślną klasę poświadczeń usługi po przechwyceniu certyfikatu usługi, który jest już wstępnie skonfigurowany w domyślnym poświadczenie usługi, i skonfigurować nowe wystąpienie poświadczeń usługi do korzystania ze wstępnie skonfigurowanych certyfikatów usługi i dodać nowe wystąpienie poświadczeń usługi do zachowań usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="4fad0-143">Aby wyświetlić informacje o wywołującym, można użyć, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4fad0-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="4fad0-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A>Zawiera informacje o oświadczeniach dotyczących bieżącego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4fad0-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="4fad0-145">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4fad0-146">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="4fad0-147">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4fad0-147">Setup Batch File</span></span>
 <span data-ttu-id="4fad0-148">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="4fad0-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="4fad0-149">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="4fad0-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="4fad0-150">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować do uruchamiania w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4fad0-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="4fad0-151">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="4fad0-151">Creating the server certificate.</span></span>

     <span data-ttu-id="4fad0-152">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="4fad0-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="4fad0-153">`%SERVER_NAME%`Zmienna określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="4fad0-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="4fad0-154">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="4fad0-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4fad0-155">Wartość domyślna w tym pliku wsadowym to localhost.</span><span class="sxs-lookup"><span data-stu-id="4fad0-155">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="4fad0-156">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="4fad0-157">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4fad0-158">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4fad0-159">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="4fad0-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="4fad0-160">Plik wsadowy instalacji został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="4fad0-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="4fad0-161">Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="4fad0-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="4fad0-162">Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="4fad0-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="4fad0-163">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="4fad0-163">To set up and build the sample</span></span>

1. <span data-ttu-id="4fad0-164">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fad0-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4fad0-165">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fad0-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="4fad0-166">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="4fad0-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="4fad0-167">Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 otwartym z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="4fad0-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="4fad0-168">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4fad0-169">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4fad0-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="4fad0-170">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="4fad0-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="4fad0-171">Uruchom usługę Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="4fad0-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="4fad0-172">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="4fad0-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="4fad0-173">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="4fad0-174">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4fad0-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="4fad0-175">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="4fad0-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="4fad0-176">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="4fad0-177">Skopiuj pliki programu Service Files do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="4fad0-178">Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="4fad0-179">Musisz mieć certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="4fad0-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="4fad0-180">Plik App. config usługi musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="4fad0-181">Można go utworzyć przy użyciu Setup. bat, jeśli ustawisz `%SERVER_NAME%` zmienną na w pełni kwalifikowaną nazwę hosta komputera, na którym zostanie uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="4fad0-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="4fad0-182">Należy pamiętać, że plik Setup. bat musi być uruchamiany z wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="4fad0-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="4fad0-183">Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="4fad0-184">Nie trzeba tego robić, chyba że certyfikat serwera zostanie wystawiony przez zaufanego wystawcy klienta.</span><span class="sxs-lookup"><span data-stu-id="4fad0-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="4fad0-185">W pliku App. config na komputerze usługi Zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="4fad0-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="4fad0-186">Na komputerze usługi Uruchom program Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad0-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="4fad0-187">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="4fad0-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="4fad0-188">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="4fad0-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="4fad0-189">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4fad0-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="4fad0-190">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4fad0-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4fad0-191">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="4fad0-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="4fad0-192">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="4fad0-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
