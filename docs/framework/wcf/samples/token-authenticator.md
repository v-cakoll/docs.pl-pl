---
title: "Wystawca uwierzytelnienia tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7404087117ec45e09495897905094690c01fbaa8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="token-authenticator"></a><span data-ttu-id="1edeb-102">Wystawca uwierzytelnienia tokenów</span><span class="sxs-lookup"><span data-stu-id="1edeb-102">Token Authenticator</span></span>
<span data-ttu-id="1edeb-103">W tym przykładzie pokazano, jak do zaimplementowania niestandardowego wystawcy uwierzytelnienia tokenu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="1edeb-104">Wystawcy uwierzytelnienia tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do sprawdzania poprawności tokenu używane z komunikatu, sprawdzania jest spójny, czy uwierzytelnianie tożsamość skojarzona z tokenem.</span><span class="sxs-lookup"><span data-stu-id="1edeb-104">A token authenticator in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>  
  
 <span data-ttu-id="1edeb-105">Niestandardowe wystawcy uwierzytelnienia tokenu są przydatne w wielu przypadkach, takich jak:</span><span class="sxs-lookup"><span data-stu-id="1edeb-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>  
  
-   <span data-ttu-id="1edeb-106">Jeśli chcesz przesłonić domyślny mechanizm uwierzytelniania, skojarzone z tokenem.</span><span class="sxs-lookup"><span data-stu-id="1edeb-106">When you want to override the default authentication mechanism associated with a token.</span></span>  
  
-   <span data-ttu-id="1edeb-107">Gdy tworzysz niestandardowy token.</span><span class="sxs-lookup"><span data-stu-id="1edeb-107">When you are building a custom token.</span></span>  
  
 <span data-ttu-id="1edeb-108">W tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="1edeb-108">This sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="1edeb-109">Jak klient może uwierzytelnić przy użyciu pary nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="1edeb-109">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="1edeb-110">Jak serwer można sprawdzić poprawności poświadczeń klienta przy użyciu niestandardowego wystawcy uwierzytelnienia tokenu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-110">How the server can validate the client credentials using a custom token authenticator.</span></span>  
  
-   <span data-ttu-id="1edeb-111">Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodu usługi wiąże się przy użyciu niestandardowego wystawcy uwierzytelnienia tokenu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-111">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code ties in with the custom token authenticator.</span></span>  
  
-   <span data-ttu-id="1edeb-112">W jaki sposób serwer mogą być uwierzytelniane za pomocą certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="1edeb-112">How the server can be authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="1edeb-113">W tym przykładzie pokazano, jak tożsamość obiektu wywołującego jest dostępny z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] po procesie uwierzytelniania tokenu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="1edeb-113">This sample also shows how the caller's identity is accessible from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="1edeb-114">Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config.</span><span class="sxs-lookup"><span data-stu-id="1edeb-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="1edeb-115">Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1edeb-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="1edeb-116">Powiązanie jest skonfigurowane z normą `wsHttpBinding`, tryb zabezpieczeń, ustawiono na wiadomości - domyślnego trybu `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="1edeb-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="1edeb-117">W tym przykładzie ustawia standardowego `wsHttpBinding` uwierzytelniania nazwa użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="1edeb-118">Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="1edeb-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="1edeb-119">`securityCredentials` Zachowanie pozwala określić certyfikat usługi.</span><span class="sxs-lookup"><span data-stu-id="1edeb-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="1edeb-120">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewnienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1edeb-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="1edeb-121">Następująca konfiguracja odwołuje się do certyfikatu localhost zainstalowane podczas instalacji próbki zgodnie z opisem w poniższych instrukcjach instalacji.</span><span class="sxs-lookup"><span data-stu-id="1edeb-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
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
  
 <span data-ttu-id="1edeb-122">Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="1edeb-123">Klient powiązanie jest skonfigurowany z użyciem odpowiednich `Mode` i `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="1edeb-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="1edeb-124">Implementacja klienta ustawia nazwę użytkownika i hasło do użycia.</span><span class="sxs-lookup"><span data-stu-id="1edeb-124">The client implementation sets the user name and password to use.</span></span>  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a><span data-ttu-id="1edeb-125">Wystawcy uwierzytelnienia tokenu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1edeb-125">Custom Token Authenticator</span></span>  
 <span data-ttu-id="1edeb-126">Poniższe kroki umożliwiają utworzenie niestandardowego wystawcy uwierzytelnienia tokenu:</span><span class="sxs-lookup"><span data-stu-id="1edeb-126">Use the following steps to create a custom token authenticator:</span></span>  
  
1.  <span data-ttu-id="1edeb-127">Pisanie niestandardowych wystawcy uwierzytelnienia tokenu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-127">Write a custom token authenticator.</span></span>  
  
     <span data-ttu-id="1edeb-128">Przykład implementuje niestandardowego wystawcy uwierzytelnienia tokenu sprawdzania, czy nazwa użytkownika ma format prawidłowy adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="1edeb-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="1edeb-129">Dziedziczy <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="1edeb-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="1edeb-130">Najważniejsze metody tej klasy jest <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="1edeb-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="1edeb-131">W przypadku tej metody, wystawcą uwierzytelnienia weryfikuje format nazwy użytkownika oraz że nazwa hosta nie jest z domeny nieautoryzowany.</span><span class="sxs-lookup"><span data-stu-id="1edeb-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="1edeb-132">Jeśli spełnione są oba warunki, a następnie zwraca kolekcję tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystąpień, które są następnie używane do zapewnienia oświadczenia, które reprezentują informacje przechowywane w tokenie nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1edeb-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>  
  
    ```  
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
  
2.  <span data-ttu-id="1edeb-133">Podaj zwróconego przez wystawcę uwierzytelnienia tokenów niestandardowe zasady autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="1edeb-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>  
  
     <span data-ttu-id="1edeb-134">W tym przykładzie przedstawiono własną implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> o nazwie `UnconditionalPolicy` zwracającą zestaw oświadczeń i tożsamości, które zostały przekazane do niego w jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1edeb-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>  
  
    ```  
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
  
3.  <span data-ttu-id="1edeb-135">Pisanie niestandardowych zabezpieczeń Menedżer tokenów.</span><span class="sxs-lookup"><span data-stu-id="1edeb-135">Write a custom security token manager.</span></span>  
  
     <span data-ttu-id="1edeb-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> obiektów, które są przekazywane do niego w `CreateSecurityTokenAuthenticator` metody.</span><span class="sxs-lookup"><span data-stu-id="1edeb-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="1edeb-137">Menedżer tokenów zabezpieczających umożliwia również tworzenie dostawcy tokenów i serializatorów tokenu, ale te nie są objęte w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1edeb-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="1edeb-138">W tym przykładzie Menedżer tokenów zabezpieczających niestandardowych dziedziczy <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenAuthenticator` metody zwracane wystawcy uwierzytelnienia tokenu niestandardowej nazwy użytkownika w przypadku przekazany wymagania tokenu wskazywać tego uwierzytelniania nazwa użytkownika jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="1edeb-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="1edeb-139">Wpisz poświadczenia usługi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="1edeb-139">Write a custom service credential.</span></span>  
  
     <span data-ttu-id="1edeb-140">Klasa poświadczenia usługi jest używana do reprezentowania poświadczenia, które są skonfigurowane dla usługi i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i serializatorów tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1edeb-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
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
  
5.  <span data-ttu-id="1edeb-141">Skonfiguruj usługę, aby użyć poświadczeń usługi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="1edeb-141">Configure the service to use the custom service credential.</span></span>  
  
     <span data-ttu-id="1edeb-142">Aby usługa ma używać poświadczeń usługi niestandardowej firma Microsoft usunąć domyślną klasę poświadczeń usługi po przechwyceniu certyfikat usługi, który jest już wstępnie skonfigurowane w domyślnych poświadczeń usługi, a następnie skonfiguruj nowe poświadczenie usługi wystąpienie, które korzystają z certyfikatów usługi wstępnie skonfigurowane i dodać tego nowego wystąpienia poświadczeń usługi do zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="1edeb-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 <span data-ttu-id="1edeb-143">Aby wyświetlić informacje o wywołującym, można użyć <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1edeb-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="1edeb-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Zawiera oświadczenia informacje o bieżącym wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1edeb-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 <span data-ttu-id="1edeb-145">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1edeb-146">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-146">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="1edeb-147">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="1edeb-147">Setup Batch File</span></span>  
 <span data-ttu-id="1edeb-148">Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia aplikacji hostowania samoobsługowego, który wymaga serwera zabezpieczeń opartego na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="1edeb-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="1edeb-149">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="1edeb-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="1edeb-150">Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1edeb-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
-   <span data-ttu-id="1edeb-151">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="1edeb-151">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="1edeb-152">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="1edeb-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="1edeb-153">`%SERVER_NAME%` Zmiennej określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="1edeb-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="1edeb-154">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="1edeb-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="1edeb-155">Domyślnie ten plik wsadowy jest localhost.</span><span class="sxs-lookup"><span data-stu-id="1edeb-155">The default in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="1edeb-156">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-156">Installing the server certificate into client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="1edeb-157">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1edeb-158">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1edeb-159">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="1edeb-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1edeb-160">Instalacyjny plik wsadowy jest przeznaczony do uruchamiania z wiersza polecenia systemu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1edeb-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="1edeb-161">Wymaga ona, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="1edeb-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="1edeb-162">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia systemu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1edeb-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="1edeb-163">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="1edeb-163">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="1edeb-164">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1edeb-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1edeb-165">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1edeb-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1edeb-166">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="1edeb-166">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="1edeb-167">Uruchom z folderu instalacji próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1edeb-167">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="1edeb-168">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-168">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1edeb-169">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1edeb-169">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="1edeb-170">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1edeb-170">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="1edeb-171">Uruchom service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="1edeb-171">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="1edeb-172">Uruchom client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="1edeb-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="1edeb-173">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-173">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="1edeb-174">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1edeb-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1edeb-175">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="1edeb-175">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="1edeb-176">Utwórz katalog na komputerze usługi dla usługi danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="1edeb-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="1edeb-177">Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="1edeb-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="1edeb-178">Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="1edeb-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="1edeb-179">Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="1edeb-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="1edeb-180">Usługa pliku App.config trzeba zaktualizować do uwzględnienia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1edeb-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="1edeb-181">Można go utworzyć przy użyciu pliku Setup.bat, jeśli ustawisz `%SERVER_NAME%` zmiennych hosta w pełni kwalifikowaną nazwę komputera, na którym uruchomiona jest usługa.</span><span class="sxs-lookup"><span data-stu-id="1edeb-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="1edeb-182">Należy pamiętać, że plik pliku setup.bat należy uruchomić z wiersza polecenia programu Visual Studio została otwarta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="1edeb-182">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="1edeb-183">Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="1edeb-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="1edeb-184">Nie trzeba w tym celu z wyjątkiem po wystawieniu certyfikatu serwera przez klienta zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="1edeb-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="1edeb-185">W pliku App.config na komputerze usługi Zmień wartość adres podstawowy, aby określić nazwę komputera w pełni kwalifikowaną zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="1edeb-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="1edeb-186">Na komputerze, usługi uruchom service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1edeb-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="1edeb-187">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1edeb-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="1edeb-188">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="1edeb-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="1edeb-189">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1edeb-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="1edeb-190">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1edeb-190">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1edeb-191">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="1edeb-191">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="1edeb-192">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="1edeb-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edeb-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1edeb-193">See Also</span></span>
