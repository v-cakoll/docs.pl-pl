---
title: Zasady autoryzacji
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463946"
---
# <a name="authorization-policy"></a><span data-ttu-id="26461-102">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="26461-102">Authorization Policy</span></span>

<span data-ttu-id="26461-103">W tym przykładzie pokazano, jak zaimplementować niestandardowe zasady autoryzacji oświadczeń i skojarzonego menedżera autoryzacji usługi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="26461-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="26461-104">Jest to przydatne, gdy usługa sprawia, że oparte na oświadczenia kontroli dostępu do operacji usługi i przed kontroli dostępu, przyznaje wywołującemu pewne prawa.</span><span class="sxs-lookup"><span data-stu-id="26461-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="26461-105">W tym przykładzie przedstawiono zarówno proces dodawania oświadczeń, jak i proces sprawdzania dostępu względem sfinalizowanego zestawu oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="26461-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="26461-106">Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="26461-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="26461-107">Domyślnie za `wsHttpBinding` pomocą powiązania nazwa użytkownika i hasło dostarczone przez klienta są używane do logowania do prawidłowego konta systemu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="26461-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="26461-108">W tym przykładzie pokazano, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> jak korzystać z niestandardowego do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="26461-109">Ponadto w tym przykładzie pokazano klienta uwierzytelniającego się w usłudze przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="26461-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="26461-110">W tym przykładzie <xref:System.IdentityModel.Policy.IAuthorizationPolicy> <xref:System.ServiceModel.ServiceAuthorizationManager>przedstawiono implementację i , które między nimi udzielają dostępu do określonych metod usługi dla określonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="26461-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="26461-111">Ten przykład jest oparty na [nazwę użytkownika zabezpieczeń wiadomości,](../../../../docs/framework/wcf/samples/message-security-user-name.md)ale pokazuje, <xref:System.ServiceModel.ServiceAuthorizationManager> jak wykonać transformację oświadczenia przed wywoływane.</span><span class="sxs-lookup"><span data-stu-id="26461-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="26461-112">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="26461-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="26461-113">Podsumowując, w tym przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="26461-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="26461-114">Klient może być uwierzytelniony przy użyciu nazwy użytkownika-hasła.</span><span class="sxs-lookup"><span data-stu-id="26461-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="26461-115">Klient może być uwierzytelniony przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="26461-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="26461-116">Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego `UsernamePassword` walidatora.</span><span class="sxs-lookup"><span data-stu-id="26461-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="26461-117">Serwer jest uwierzytelniony przy użyciu certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="26461-118">Serwer może <xref:System.ServiceModel.ServiceAuthorizationManager> służyć do kontrolowania dostępu do niektórych metod w usłudze.</span><span class="sxs-lookup"><span data-stu-id="26461-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="26461-119">Jak wdrożyć <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="26461-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="26461-120">Usługa udostępnia dwa punkty końcowe do komunikowania się z usługą, zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="26461-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="26461-121">Jedno powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` powiązania, które używa uwierzytelniania w uchronienia klienta i uwierzytelniania nazwy użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="26461-122">Inne powiązanie jest skonfigurowane `wsHttpBinding` przy użyciu standardowego powiązania, które używa usługi WS-Security i uwierzytelniania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="26461-123">[ \<Zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) określa, że poświadczenia użytkownika mają być używane do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="26461-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="26461-124">Certyfikat serwera musi zawierać taką `SubjectName` samą `findValue` wartość właściwości jak atrybut w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="26461-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="26461-125">Każda konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, bezwzględny adres dla punktu końcowego usługi, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="26461-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="26461-126">Powiązanie klienta jest skonfigurowane w odpowiednim trybie zabezpieczeń określonym w `clientCredentialType` tym przypadku w>[ \<zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) i jak określono w [ \<komunikacie>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="26461-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="26461-127">W przypadku punktu końcowego opartego na nazwie użytkownika implementacja klienta ustawia nazwę użytkownika i hasło do użycia.</span><span class="sxs-lookup"><span data-stu-id="26461-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="26461-128">W przypadku punktu końcowego opartego na certyfikatach implementacja klienta ustawia certyfikat klienta do użycia.</span><span class="sxs-lookup"><span data-stu-id="26461-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="26461-129">W tym przykładzie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> użyto niestandardowego sprawdzania poprawności nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="26461-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="26461-130">Przykład implementuje, `MyCustomUserNamePasswordValidator`pochodzące <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>z .</span><span class="sxs-lookup"><span data-stu-id="26461-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="26461-131">Więcej informacji <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> można znaleźć w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="26461-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="26461-132">W celu wykazania integracji z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, ten przykład niestandardowego <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> walidatora implementuje metodę akceptowania par nazwy użytkownika/hasła, w których nazwa użytkownika jest zgodna z hasłem, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="26461-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="26461-133">Po zaimplementowaniu walidatora w kodzie usługi host usługi musi zostać poinformowany o wystąpieniu walidatora do użycia.</span><span class="sxs-lookup"><span data-stu-id="26461-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="26461-134">Odbywa się to przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="26461-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="26461-135">Lub można zrobić to samo w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="26461-135">Or you can do the same thing in configuration:</span></span>

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

<span data-ttu-id="26461-136">Windows Communication Foundation (WCF) udostępnia bogaty model oparty na oświadczeniach do przeprowadzania kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="26461-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="26461-137">Obiekt <xref:System.ServiceModel.ServiceAuthorizationManager> jest używany do wykonywania kontroli dostępu i określić, czy oświadczenia skojarzone z klientem spełniają wymagania niezbędne do uzyskania dostępu do metody usługi.</span><span class="sxs-lookup"><span data-stu-id="26461-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="26461-138">Na potrzeby demonstracji w tym przykładzie <xref:System.ServiceModel.ServiceAuthorizationManager> przedstawiono implementację, która implementuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę, aby umożliwić `http://example.com/claims/allowedoperation` użytkownikowi dostęp do metod opartych na oświadczeniach typu, którego wartością jest identyfikator URI akcji operacji, która może być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="26461-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="26461-139">Po zaimplementowaniu niestandardowego <xref:System.ServiceModel.ServiceAuthorizationManager> hosta usługi <xref:System.ServiceModel.ServiceAuthorizationManager> musi być informowany o do użycia.</span><span class="sxs-lookup"><span data-stu-id="26461-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="26461-140">Odbywa się to w sposób pokazany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="26461-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="26461-141">Podstawową <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metodą do <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> zaimplementowania jest metoda.</span><span class="sxs-lookup"><span data-stu-id="26461-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="26461-142">Poprzedni kod pokazuje, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> jak metoda sprawdza, czy nie dodano żadnych nowych oświadczeń, które wpływają na przetwarzanie i dodaje określone oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="26461-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="26461-143">Oświadczenia, które są dozwolone są `GetAllowedOpList` uzyskiwane z metody, która jest implementowana do zwracania określonej listy operacji, które użytkownik może wykonać.</span><span class="sxs-lookup"><span data-stu-id="26461-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="26461-144">Zasady autoryzacji dodaje oświadczenia dotyczące dostępu do określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="26461-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="26461-145">Jest to później <xref:System.ServiceModel.ServiceAuthorizationManager> używane przez do wykonywania decyzji dotyczących sprawdzania dostępu.</span><span class="sxs-lookup"><span data-stu-id="26461-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="26461-146">Po zaimplementowaniu niestandardowego <xref:System.IdentityModel.Policy.IAuthorizationPolicy> host usługi musi zostać poinformowany o zasadach autoryzacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="26461-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="26461-147">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="26461-148">Klient pomyślnie wywołuje Add, Odejmij i wiele metod i pobiera komunikat "Odmowa dostępu" podczas próby wywołania Metody Dzielenia.</span><span class="sxs-lookup"><span data-stu-id="26461-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="26461-149">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="26461-150">Plik wsadowy instalatora</span><span class="sxs-lookup"><span data-stu-id="26461-150">Setup Batch File</span></span>

<span data-ttu-id="26461-151">Plik wsadowy Setup.bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie, która wymaga zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="26461-152">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować w celu uruchomienia w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="26461-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="26461-153">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-153">Creating the server certificate.</span></span>

    <span data-ttu-id="26461-154">Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="26461-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="26461-155">Zmienna %SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="26461-156">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="26461-157">Wartością domyślną jest localhost.</span><span class="sxs-lookup"><span data-stu-id="26461-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="26461-158">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="26461-159">Następujące wiersze w pliku wsadowym Setup.bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="26461-160">Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki.</span><span class="sxs-lookup"><span data-stu-id="26461-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="26461-161">Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="26461-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="26461-162">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-162">Creating the client certificate.</span></span>

    <span data-ttu-id="26461-163">Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="26461-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="26461-164">Zmienna %USER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="26461-165">Ta wartość jest ustawiona na "test1", `IAuthorizationPolicy` ponieważ jest to nazwa, która jest wyszukany.</span><span class="sxs-lookup"><span data-stu-id="26461-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="26461-166">Jeśli zmienisz wartość %USER_NAME%, musisz zmienić odpowiednią `IAuthorizationPolicy.Evaluate` wartość w metodzie.</span><span class="sxs-lookup"><span data-stu-id="26461-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="26461-167">Certyfikat jest przechowywany w sklepie Mój (osobisty) w lokalizacji sklepu CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="26461-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="26461-168">Instalowanie certyfikatu klienta w magazynie zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="26461-169">Następujące wiersze w pliku wsadowym Setup.bat kopiują certyfikat klienta do magazynu zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="26461-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="26461-170">Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="26461-171">Jeśli masz już certyfikat, który jest zakorzeniony w zaufanym certyfikacie głównym — na przykład certyfikatowi wystawionemu przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów serwera certyfikatem klienta nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="26461-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="26461-172">Aby skonfigurować i utworzyć próbkę</span><span class="sxs-lookup"><span data-stu-id="26461-172">To set up and build the sample</span></span>

1. <span data-ttu-id="26461-173">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26461-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="26461-174">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, należy użyć następujących instrukcji.</span><span class="sxs-lookup"><span data-stu-id="26461-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="26461-175">Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="26461-176">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="26461-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="26461-177">Otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora i uruchom *plik Setup.bat* z przykładowego folderu instalacji.</span><span class="sxs-lookup"><span data-stu-id="26461-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="26461-178">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.</span><span class="sxs-lookup"><span data-stu-id="26461-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="26461-179">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dewelopera dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26461-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="26461-180">Zmienna środowiskowa PATH ustawiona w wierszu polecenia dewelopera dla programu Visual Studio wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt *Setup.bat.*</span><span class="sxs-lookup"><span data-stu-id="26461-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="26461-181">Uruchom program Service.exe z *pliku service\bin*.</span><span class="sxs-lookup"><span data-stu-id="26461-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="26461-182">Uruchom program Client.exe z *pliku \client\bin*.</span><span class="sxs-lookup"><span data-stu-id="26461-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="26461-183">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="26461-184">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="26461-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="26461-185">Aby uruchomić próbkę na różnych komputerach</span><span class="sxs-lookup"><span data-stu-id="26461-185">To run the sample across computers</span></span>

1. <span data-ttu-id="26461-186">Utwórz katalog na komputerze usługowym.</span><span class="sxs-lookup"><span data-stu-id="26461-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="26461-187">Skopiuj pliki programu serwisowego z *\service\bin* do katalogu na komputerze usługowym.</span><span class="sxs-lookup"><span data-stu-id="26461-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="26461-188">Skopiuj również pliki Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat do komputera serwisowego.</span><span class="sxs-lookup"><span data-stu-id="26461-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="26461-189">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="26461-190">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="26461-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="26461-191">Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="26461-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="26461-192">Na serwerze `setup.bat service` uruchom w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="26461-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="26461-193">Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie *Service.cer*.</span><span class="sxs-lookup"><span data-stu-id="26461-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="26461-194">Edytuj *service.exe.config,* aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="26461-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="26461-195">Zmień również **nazwę komputera** \<w serwisie>/\<baseAddresses> element z localhost na w pełni kwalifikowaną nazwę komputera usługowego.</span><span class="sxs-lookup"><span data-stu-id="26461-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="26461-196">Skopiuj plik *Service.cer* z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="26461-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="26461-197">Na kliencie `setup.bat client` uruchom w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="26461-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="26461-198">Uruchamianie `setup.bat` `client` z argumentem tworzy certyfikat klienta o nazwie **test1** i eksportuje certyfikat klienta do pliku o nazwie *Client.cer*.</span><span class="sxs-lookup"><span data-stu-id="26461-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="26461-199">W pliku *Client.exe.config* na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="26461-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="26461-200">W tym celu można zastąpić **hosta lokalnego** w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="26461-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="26461-201">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="26461-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="26461-202">Na kliencie uruchom *plik ImportServiceCert.bat* w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="26461-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="26461-203">Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu **CurrentUser — TrustedPeople.**</span><span class="sxs-lookup"><span data-stu-id="26461-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="26461-204">Na serwerze uruchom *plik ImportClientCert.bat* w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="26461-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="26461-205">Spowoduje to zaimportowanie certyfikatu klienta z pliku Client.cer do magazynu **LocalMachine — TrustedPeople.**</span><span class="sxs-lookup"><span data-stu-id="26461-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="26461-206">Na komputerze serwera uruchom program Service.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="26461-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="26461-207">Na komputerze klienckim uruchom program Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="26461-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="26461-208">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="26461-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="26461-209">Czyszczenie po próbce</span><span class="sxs-lookup"><span data-stu-id="26461-209">Clean up after the sample</span></span>

<span data-ttu-id="26461-210">Aby wyczyścić po próbce, uruchom *Cleanup.bat* w folderze próbek po zakończeniu uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="26461-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="26461-211">Spowoduje to usunięcie certyfikatów serwera i klienta z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="26461-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="26461-212">Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="26461-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="26461-213">Jeśli zostały uruchomione próbki WCF, które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w currentuser — TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="26461-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="26461-214">Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="26461-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
