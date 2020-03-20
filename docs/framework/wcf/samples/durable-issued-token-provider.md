---
title: Niezawodny dostawca wystawionych tokenów
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144750"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="d4799-102">Niezawodny dostawca wystawionych tokenów</span><span class="sxs-lookup"><span data-stu-id="d4799-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="d4799-103">W tym przykładzie pokazano, jak zaimplementować niestandardowego dostawcy tokenu wystawionego przez klienta niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d4799-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d4799-104">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="d4799-104">Discussion</span></span>  
 <span data-ttu-id="d4799-105">Dostawca tokenów w programie Windows Communication Foundation (WCF) służy do dostarczania poświadczeń do infrastruktury zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d4799-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="d4799-106">Dostawca tokenu w ogóle sprawdza obiekt docelowy i wystawia odpowiednie poświadczenia, dzięki czemu infrastruktura zabezpieczeń może zabezpieczyć komunikat.</span><span class="sxs-lookup"><span data-stu-id="d4799-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="d4799-107">WCF jest dostarczany z dostawcą tokenów CardSpace.</span><span class="sxs-lookup"><span data-stu-id="d4799-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="d4799-108">Dostawcy tokenów niestandardowych są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="d4799-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="d4799-109">Jeśli masz magazyn poświadczeń, z którego nie może działać wbudowany dostawca tokenu.</span><span class="sxs-lookup"><span data-stu-id="d4799-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="d4799-110">Jeśli chcesz podać własny mechanizm niestandardowy do przekształcania poświadczeń od punktu, gdy użytkownik udostępnia szczegóły, gdy klient WCF używa poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d4799-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="d4799-111">Jeśli budujesz token niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="d4799-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="d4799-112">W tym przykładzie pokazano, jak utworzyć niestandardowego dostawcy tokenów, który buforuje tokeny wystawione przez usługę tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="d4799-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="d4799-113">Podsumowując, w tym przykładzie przedstawiono następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="d4799-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="d4799-114">Jak można skonfigurować klienta za pomocą niestandardowego dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="d4799-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="d4799-115">Jak wystawione tokeny mogą być buforowane i dostarczane do klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="d4799-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="d4799-116">Sposób uwierzytelniania serwera przez klienta przy użyciu certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="d4799-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="d4799-117">Ten przykład składa się z programu konsoli klienta (Client.exe), programu konsoli usługi tokenu zabezpieczającego (Securitytokenservice.exe) i programu konsoli usługi (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="d4799-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="d4799-118">Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="d4799-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="d4799-119">Kontrakt jest definiowany `ICalculator` przez interfejs, który udostępnia operacje matematyczne (dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="d4799-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="d4799-120">Klient pobiera token zabezpieczający z usługi tokenu zabezpieczającego (STS) i sprawia, że synchroniczne żądania do usługi dla danej operacji matematycznej i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="d4799-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="d4799-121">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d4799-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4799-122">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d4799-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d4799-123">Ten przykład udostępnia kontrakt ICalculator przy użyciu [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d4799-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="d4799-124">Konfiguracja tego powiązania na kliencie jest pokazana w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4799-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows"
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="d4799-125">W `security` `wsFederationHttpBinding`elemencie `mode` wartość określa, który tryb zabezpieczeń powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="d4799-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="d4799-126">W tym przykładzie używane są zabezpieczenia `message` wiadomości, `wsFederationHttpBinding` dlatego element `security` jest `wsFederationHttpBinding`określony wewnątrz elementu .</span><span class="sxs-lookup"><span data-stu-id="d4799-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="d4799-127">Element `issuer` `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` określa adres i powiązanie dla usługi tokenu zabezpieczającego, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnić się w usłudze Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="d4799-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="d4799-128">Konfiguracja tego powiązania w usłudze jest pokazana w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4799-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType="FindBySubjectDistinguishedName"
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="d4799-129">W `security` `wsFederationHttpBinding`elemencie `mode` wartość określa, który tryb zabezpieczeń powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="d4799-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="d4799-130">W tym przykładzie używane są zabezpieczenia `message` wiadomości, `wsFederationHttpBinding` dlatego element `security` jest `wsFederationHttpBinding`określony wewnątrz elementu .</span><span class="sxs-lookup"><span data-stu-id="d4799-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="d4799-131">Element `issuerMetadata` `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` określa adres i tożsamość punktu końcowego, który może służyć do pobierania metadanych dla usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="d4799-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="d4799-132">Zachowanie usługi jest pokazane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4799-132">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine"
              storeName="TrustedPeople"
              x509FindType="FindBySubjectDistinguishedName"
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine"
                        storeName="My"
                        x509FindType="FindBySubjectDistinguishedName"
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="d4799-133">Element `issuedTokenAuthentication` wewnątrz `serviceCredentials` elementu umożliwia usługi, aby określić ograniczenia tokenów, które umożliwia klientom do przedstawienia podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="d4799-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="d4799-134">Ta konfiguracja określa, że tokeny podpisane certyfikatem, którego nazwa podmiotu jest CN = STS są akceptowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="d4799-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="d4799-135">Usługa tokenu zabezpieczającego udostępnia pojedynczy punkt końcowy przy użyciu standardowego wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="d4799-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="d4799-136">Usługa tokenu zabezpieczającego odpowiada na żądanie klientów dotyczące tokenów i, pod warunkiem, że klient uwierzytelnia się przy użyciu konta systemu Windows, wystawia token zawierający nazwę użytkownika klienta jako oświadczenie w wystawionym tokenie.</span><span class="sxs-lookup"><span data-stu-id="d4799-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="d4799-137">W ramach tworzenia tokenu usługa tokenu zabezpieczającego podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem CN=STS.</span><span class="sxs-lookup"><span data-stu-id="d4799-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="d4799-138">Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="d4799-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="d4799-139">Podczas zwracania tokenu do klienta usługa tokenu zabezpieczającego zwraca również klucz symetryczny.</span><span class="sxs-lookup"><span data-stu-id="d4799-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="d4799-140">Klient przedstawia wystawiony token do usługi Kalkulator i udowadnia, że zna klucz symetryczny, podpisując wiadomość za pomocą tego klucza.</span><span class="sxs-lookup"><span data-stu-id="d4799-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="d4799-141">Niestandardowe poświadczenia klienta i dostawca tokenów</span><span class="sxs-lookup"><span data-stu-id="d4799-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="d4799-142">Poniższe kroki pokazują, jak opracować niestandardowego dostawcy tokenu, który buforuje wystawione tokeny i zintegrować go z WCF: security.</span><span class="sxs-lookup"><span data-stu-id="d4799-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="d4799-143">Aby opracować niestandardowego dostawcę tokenów</span><span class="sxs-lookup"><span data-stu-id="d4799-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="d4799-144">Napisz niestandardowego dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="d4799-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="d4799-145">Przykład implementuje niestandardowego dostawcy tokenu, który zwraca token zabezpieczający pobrany z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d4799-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="d4799-146">Aby wykonać to zadanie, dostawca tokenu niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenProvider> wyprowadza <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> klasę i zastępuje metodę.</span><span class="sxs-lookup"><span data-stu-id="d4799-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="d4799-147">Ta metoda próbuje pobrać token z pamięci podręcznej lub jeśli token nie można znaleźć w pamięci podręcznej, pobiera token od dostawcy źródłowego, a następnie buforuje tego tokenu.</span><span class="sxs-lookup"><span data-stu-id="d4799-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="d4799-148">W obu przypadkach metoda `SecurityToken`zwraca .</span><span class="sxs-lookup"><span data-stu-id="d4799-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="d4799-149">Napisz niestandardowy menedżer tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d4799-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="d4799-150">Jest <xref:System.IdentityModel.Selectors.SecurityTokenManager> używany do <xref:System.IdentityModel.Selectors.SecurityTokenProvider> tworzenia dla <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> określonego, który jest `CreateSecurityTokenProvider` przekazywany do niego w metodzie.</span><span class="sxs-lookup"><span data-stu-id="d4799-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="d4799-151">Menedżer tokenów zabezpieczających jest również używany do tworzenia tokenów uwierzytelniaczy i serializatorów tokenów, ale nie są to objęte tym przykładem.</span><span class="sxs-lookup"><span data-stu-id="d4799-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="d4799-152">W tym przykładzie niestandardowy menedżer tokenu zabezpieczającego <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> dziedziczy z klasy i zastępuje `CreateSecurityTokenProvider` metodę zwracania dostawcy tokenu niestandardowego, gdy wymagania dotyczące tokenu przekazanego wskazują, że żądany jest wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="d4799-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="d4799-153">Napisz niestandardowe poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="d4799-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="d4799-154">Klasa poświadczeń klienta jest używana do reprezentowania poświadczeń skonfigurowanych dla serwera proxy klienta i tworzy menedżera tokenu zabezpieczającego, który jest używany do uzyskiwania wystawców uwierzytelniających token, dostawców tokenów i serializatorów tokenów.</span><span class="sxs-lookup"><span data-stu-id="d4799-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="d4799-155">Zaimplementuj pamięć podręczną tokenu.</span><span class="sxs-lookup"><span data-stu-id="d4799-155">Implement the token cache.</span></span> <span data-ttu-id="d4799-156">Przykładowa implementacja używa abstrakcyjnej klasy podstawowej, za pomocą której konsumenci danej pamięci podręcznej tokenu współdziałają z pamięcią podręczną.</span><span class="sxs-lookup"><span data-stu-id="d4799-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="d4799-157">Aby klient używał niestandardowych poświadczeń klienta, przykładowy usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="d4799-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="d4799-158">Uruchamianie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="d4799-158">Running the sample</span></span>  
 <span data-ttu-id="d4799-159">Zobacz poniższe instrukcje, aby uruchomić próbkę.</span><span class="sxs-lookup"><span data-stu-id="d4799-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="d4799-160">Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="d4799-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="d4799-161">Żądania operacji i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="d4799-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="d4799-162">Naciśnij klawisz ENTER w dowolnym okienku konsoli, aby wyłączyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="d4799-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="d4799-163">Plik wsadowy instalatora.cmd</span><span class="sxs-lookup"><span data-stu-id="d4799-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="d4799-164">Plik wsadowy Setup.cmd dołączony do tego przykładu umożliwia skonfigurowanie usługi serwera i tokenu zabezpieczającego z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="d4799-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="d4799-165">Plik wsadowy tworzy dwa certyfikaty zarówno w magazynie certyfikatów CurrentUser/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="d4799-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="d4799-166">Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które wystawia klientowi.</span><span class="sxs-lookup"><span data-stu-id="d4799-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="d4799-167">Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez usługę tokenu zabezpieczającego do szyfrowania klucza tajnego, aby usługa mogła go odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="d4799-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4799-168">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="d4799-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d4799-169">Uruchom plik Setup.cmd, aby utworzyć wymagane certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="d4799-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="d4799-170">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4799-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="d4799-171">Upewnij się, że wszystkie projekty w rozwiązaniu są zbudowane (udostępnione, RSTRSTR, usługa, SecurityTokenService i klienta).</span><span class="sxs-lookup"><span data-stu-id="d4799-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="d4799-172">Upewnij się, że usługi Service.exe i SecurityTokenService.exe są uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="d4799-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="d4799-173">Uruchom plik Client.exe.</span><span class="sxs-lookup"><span data-stu-id="d4799-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d4799-174">Aby oczyścić po próbce</span><span class="sxs-lookup"><span data-stu-id="d4799-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="d4799-175">Uruchom cleanup.cmd w folderze próbek po zakończeniu uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="d4799-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4799-176">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d4799-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4799-177">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="d4799-177">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d4799-178">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d4799-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4799-179">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d4799-179">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
