---
title: Zasady autoryzacji
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: eaf4dfc6e1f02a1cd98d9ab48af70426e8ba6151
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674368"
---
# <a name="authorization-policy"></a><span data-ttu-id="2484e-102">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="2484e-102">Authorization Policy</span></span>

<span data-ttu-id="2484e-103">Ten przykład demonstruje sposób implementacji zasad autoryzacji oświadczenia niestandardowego i skojarzona usługa niestandardowego Menedżera autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="2484e-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="2484e-104">Jest to przydatne, kiedy usług ułatwia kontrole dostępu oparta na oświadczeniach, do operacji usługi i kontroli dostępu, udziela obiekt wywołujący pewne prawa.</span><span class="sxs-lookup"><span data-stu-id="2484e-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="2484e-105">W tym przykładzie przedstawiono proces dodawania oświadczeń, a także proces ten kontrolę dostępu dla ukończonego zestaw oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="2484e-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="2484e-106">Wszystkie komunikaty aplikacji między klientem i serwerem są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="2484e-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="2484e-107">Domyślnie `wsHttpBinding` powiązania nazwy użytkownika i hasło podane przez klienta są używane do logowania się do prawidłowego konta Windows NT.</span><span class="sxs-lookup"><span data-stu-id="2484e-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="2484e-108">W tym przykładzie pokazano, jak korzystanie z niestandardowego <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-108">This sample demonstrates how to utilize a custom <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` to authenticate the client.</span></span> <span data-ttu-id="2484e-109">Ponadto ten przykład pokazuje klienta uwierzytelniania usługi przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2484e-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="2484e-110">Ten przykład pokazuje implementację <xref:System.IdentityModel.Policy.IAuthorizationPolicy> i <xref:System.ServiceModel.ServiceAuthorizationManager>, który między nimi udzielić dostępu do określonych metod usługi dla określonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2484e-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="2484e-111">Ten przykład jest oparty na [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale pokazuje, jak przeprowadzić przekształcania oświadczeń w programach starszych niż program <xref:System.ServiceModel.ServiceAuthorizationManager> wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2484e-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="2484e-112">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2484e-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="2484e-113">Podsumowując, ten przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="2484e-113">In summary, this sample demonstrates how:</span></span>

-   <span data-ttu-id="2484e-114">Klient może zostać uwierzytelniony przy użyciu nazwy — hasło użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2484e-114">The client can be authenticated using a user name-password.</span></span>

-   <span data-ttu-id="2484e-115">Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2484e-115">The client can be authenticated using an X.509 certificate.</span></span>

-   <span data-ttu-id="2484e-116">Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego `UsernamePassword` modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="2484e-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

-   <span data-ttu-id="2484e-117">Serwer jest uwierzytelniany przy użyciu certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-117">The server is authenticated using the server's X.509 certificate.</span></span>

-   <span data-ttu-id="2484e-118">Serwer może używać <xref:System.ServiceModel.ServiceAuthorizationManager> kontrolować dostęp do pewnych metod w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2484e-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

-   <span data-ttu-id="2484e-119">Jak zaimplementować <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="2484e-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="2484e-120">Usługa udostępnia dwa punkty końcowe dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2484e-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2484e-121">Jedno powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, który używa uwierzytelniania nazwy użytkownika protokołu WS-Security i klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="2484e-122">Inne powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, który używa uwierzytelniania certyfikatu usługi WS-Security i klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="2484e-123">[ \<Zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Określa, czy poświadczenia użytkownika mają być używane do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="2484e-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="2484e-124">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` właściwość jako `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="2484e-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
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
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

<span data-ttu-id="2484e-125">Każdej konfiguracji punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia.</span><span class="sxs-lookup"><span data-stu-id="2484e-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="2484e-126">Powiązanie skonfigurowaniu klienta w trybie zabezpieczeń odpowiednich podaną w tym przypadku w [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) i `clientCredentialType` określonej [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2484e-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="2484e-127">Dla użytkowników na podstawie nazwy punktu końcowego implementacji klienta ustawia nazwę użytkownika i hasło do użycia.</span><span class="sxs-lookup"><span data-stu-id="2484e-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

<span data-ttu-id="2484e-128">Do endpoint opartego na certyfikatach implementacji klienta ustawia certyfikat klienta do użycia.</span><span class="sxs-lookup"><span data-stu-id="2484e-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

<span data-ttu-id="2484e-129">W tym przykładzie użyto niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> do weryfikowania nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="2484e-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="2484e-130">Implementuje próbki `MyCustomUserNamePasswordValidator`, pochodzącej z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="2484e-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="2484e-131">Zobacz dokumentację na temat <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="2484e-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="2484e-132">Na potrzeby demonstrowania integracji z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, w tym przykładzie niestandardowego modułu weryfikacji implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę, aby zaakceptować pary nazwa/hasło użytkownika, jeśli nazwa użytkownika odpowiada hasło, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2484e-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

<span data-ttu-id="2484e-133">Po wdrożeniu modułu sprawdzania poprawności jest w kodzie usługi hosta usługi muszą zostać powiadomieni o wystąpieniu weryfikacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="2484e-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="2484e-134">Odbywa się przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2484e-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="2484e-135">Lub można zrobić to samo w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="2484e-135">Or you can do the same thing in configuration:</span></span>

```xml
<behavior ...>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

<span data-ttu-id="2484e-136">Windows Communication Foundation (WCF) zapewnia rozbudowane modelu opartego na oświadczeniach do wykonywania kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="2484e-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="2484e-137"><xref:System.ServiceModel.ServiceAuthorizationManager> Obiekt jest używany do wykonywania kontroli dostępu i określić, czy oświadczenia skojarzone z klientami spełnia wymagania niezbędne do uzyskania dostępu do metody usługi.</span><span class="sxs-lookup"><span data-stu-id="2484e-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="2484e-138">Dla celów demonstracyjnych, w tym przykładzie pokazano implementację <xref:System.ServiceModel.ServiceAuthorizationManager> implementującej <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę, aby umożliwić użytkownikowi dostęp do metod na podstawie oświadczeń typu http://example.com/claims/allowedoperation którego wartością jest identyfikator URI akcji operacji, która jest może zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="2484e-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type http://example.com/claims/allowedoperation whose value is the Action URI of the operation that is allowed to be called.</span></span>

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

<span data-ttu-id="2484e-139">Raz niestandardowe <xref:System.ServiceModel.ServiceAuthorizationManager> jest zaimplementowana, hosta usługi musi być poinformowany o <xref:System.ServiceModel.ServiceAuthorizationManager> do użycia.</span><span class="sxs-lookup"><span data-stu-id="2484e-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="2484e-140">Odbywa się, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2484e-140">This is done as shown in the following code.</span></span>

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="2484e-141">Podstawowy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metody do zaimplementowania <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody.</span><span class="sxs-lookup"><span data-stu-id="2484e-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

<span data-ttu-id="2484e-142">W poprzednim kodzie sposób, w jaki <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda sprawdza, czy nie nowych oświadczeń został dodany, które wpływają na przetwarzanie i dodaje określonych oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="2484e-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="2484e-143">Oświadczenia, które są dozwolone są uzyskiwane z `GetAllowedOpList` metody, która jest zaimplementowana, aby zwrócić listę operacji, które użytkownik może wykonywać.</span><span class="sxs-lookup"><span data-stu-id="2484e-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="2484e-144">Zasady autoryzacji dodaje oświadczenia do uzyskiwania dostępu do określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="2484e-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="2484e-145">Jest on używany później przez <xref:System.ServiceModel.ServiceAuthorizationManager> przeprowadzić decyzji dotyczących kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="2484e-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="2484e-146">Gdy niestandardowe <xref:System.IdentityModel.Policy.IAuthorizationPolicy> jest implementowana, host usługi musi być poinformowany o zasady autoryzacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="2484e-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="2484e-147">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2484e-148">Klient pomyślnie wywołuje dodawania, odejmowania i wiele metod i pobiera komunikat "Odmowa dostępu" podczas próby wywołania metody dzielenia.</span><span class="sxs-lookup"><span data-stu-id="2484e-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="2484e-149">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="2484e-150">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="2484e-150">Setup Batch File</span></span>

<span data-ttu-id="2484e-151">Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia aplikacji własnego wymagającego zabezpieczenia oparte na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="2484e-152">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="2484e-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

-   <span data-ttu-id="2484e-153">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-153">Creating the server certificate.</span></span>

     <span data-ttu-id="2484e-154">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2484e-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="2484e-155">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2484e-156">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2484e-157">Wartość domyślna to hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2484e-157">The default value is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="2484e-158">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-158">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="2484e-159">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="2484e-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2484e-160">Ten krok jest wymagany, ponieważ certyfikaty, które są generowane przez Makecert.exe nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2484e-161">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="2484e-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="2484e-162">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-162">Creating the client certificate.</span></span>

     <span data-ttu-id="2484e-163">Następujące wiersze z pliku wsadowego Setup.bat utworzenia certyfikatu klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2484e-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="2484e-164">% Zmienna % nazwa_użytkownika Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2484e-165">Ta wartość jest równa "test1", ponieważ jest to nazwa `IAuthorizationPolicy` szuka.</span><span class="sxs-lookup"><span data-stu-id="2484e-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="2484e-166">Jeśli zmienisz wartość % nazwa_użytkownika należy zmienić odpowiednie wartości w `IAuthorizationPolicy.Evaluate` metody.</span><span class="sxs-lookup"><span data-stu-id="2484e-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

     <span data-ttu-id="2484e-167">Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="2484e-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="2484e-168">Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-168">Installing the client certificate into server's trusted certificate store.</span></span>

     <span data-ttu-id="2484e-169">Następujące wiersze w pliku wsadowym Setup.bat skopiuj certyfikat klienta do magazynu osób zaufanych.</span><span class="sxs-lookup"><span data-stu-id="2484e-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="2484e-170">Ten krok jest wymagany, ponieważ certyfikaty, które są generowane przez Makecert.exe nie niejawnie cieszą się zaufaniem systemu serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="2484e-171">Jeśli masz już certyfikat, który jest ścieżką w zaufany certyfikat główny — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów serwera za pomocą certyfikatu klienta nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="2484e-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2484e-172">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="2484e-172">To set up and build the sample</span></span>

1. <span data-ttu-id="2484e-173">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2484e-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="2484e-174">Do uruchomienia przykładu w konfiguracji o jednym lub wielu komputerze, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2484e-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="2484e-175">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2484e-176">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="2484e-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="2484e-177">Otwórz wiersz polecenia programisty dla programu Visual Studio z uprawnieniami administratora i uruchom *Setup.bat* z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="2484e-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="2484e-178">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="2484e-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2484e-179">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dla deweloperów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2484e-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="2484e-180">Zmiennej środowiskowej PATH ustawiona w wierszu polecenia dla deweloperów dla programu Visual Studio wskazuje katalog, który zawiera wymagane przez pliki wykonywalne *Setup.bat* skryptu.</span><span class="sxs-lookup"><span data-stu-id="2484e-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="2484e-181">Uruchom Service.exe z *service\bin*.</span><span class="sxs-lookup"><span data-stu-id="2484e-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="2484e-182">Uruchom Client.exe z *\client\bin*.</span><span class="sxs-lookup"><span data-stu-id="2484e-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="2484e-183">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-183">Client activity is displayed on the client console application.</span></span>

  <span data-ttu-id="2484e-184">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2484e-184">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2484e-185">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="2484e-185">To run the sample across computers</span></span>

1. <span data-ttu-id="2484e-186">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="2484e-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="2484e-187">Skopiuj pliki programu usługi z *\service\bin* do katalogu na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="2484e-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="2484e-188">Także skopiować pliki Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat, aby komputer z usługą.</span><span class="sxs-lookup"><span data-stu-id="2484e-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="2484e-189">Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="2484e-190">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2484e-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2484e-191">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="2484e-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="2484e-192">Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2484e-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="2484e-193">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie *Service.cer*.</span><span class="sxs-lookup"><span data-stu-id="2484e-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="2484e-194">Edytuj *Service.exe.config* aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="2484e-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="2484e-195">Również zmienić **computername** w \<usługi > /\<baseAddresses > element z hostem lokalnym do w pełni kwalifikowanej nazwy komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="2484e-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="2484e-196">Kopiuj *Service.cer* plików z katalogu usługi katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2484e-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="2484e-197">Na komputerze klienckim, należy uruchomić `setup.bat client` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2484e-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="2484e-198">Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie **test1** i eksportuje certyfikat klienta do pliku o nazwie *Client.cer*.</span><span class="sxs-lookup"><span data-stu-id="2484e-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="2484e-199">W *Client.exe.config* pliku na komputerze klienckim, zmień wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="2484e-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="2484e-200">To zrobić przez zastąpienie **localhost** z w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="2484e-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="2484e-201">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2484e-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="2484e-202">Na komputerze klienckim, należy uruchomić *ImportServiceCert.bat* w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2484e-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="2484e-203">Zaimportowany certyfikat usługi z pliku Service.cer do **CurrentUser - TrustedPeople** przechowywania.</span><span class="sxs-lookup"><span data-stu-id="2484e-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="2484e-204">Na serwerze, uruchom *ImportClientCert.bat* w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="2484e-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="2484e-205">Zaimportowany certyfikat klienta z pliku Client.cer do **LocalMachine - TrustedPeople** przechowywania.</span><span class="sxs-lookup"><span data-stu-id="2484e-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="2484e-206">Na komputerze serwera uruchomić Service.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2484e-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="2484e-207">Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2484e-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

   <span data-ttu-id="2484e-208">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2484e-208">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="2484e-209">Wyczyść zasoby po ukończeniu próbki</span><span class="sxs-lookup"><span data-stu-id="2484e-209">Clean up after the sample</span></span>

<span data-ttu-id="2484e-210">Aby wyczyścić zasoby po próbki, należy uruchomić *Cleanup.bat* w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="2484e-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="2484e-211">Spowoduje to usunięcie certyfikaty klienta i serwera z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2484e-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="2484e-212">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="2484e-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2484e-213">Jeśli uruchamiasz przykłady WCF, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople przechowywania.</span><span class="sxs-lookup"><span data-stu-id="2484e-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2484e-214">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2484e-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>