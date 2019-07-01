---
title: Niezawodny dostawca wystawionych tokenów
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: bfe8f8bb8c3775760bc69031e338a156d690ab25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487599"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="07688-102">Niezawodny dostawca wystawionych tokenów</span><span class="sxs-lookup"><span data-stu-id="07688-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="07688-103">Ten przykład demonstruje sposób implementacji niestandardowego klienta, dostawca wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="07688-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="07688-104">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="07688-104">Discussion</span></span>  
 <span data-ttu-id="07688-105">Dostawca tokenu w Windows Communication Foundation (WCF) umożliwia podanie poświadczeń w celu infrastruktura zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="07688-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="07688-106">Dostawcy tokenu, który sprawdza ogólnie rzecz biorąc, element docelowy i problemy odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="07688-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="07688-107">Usługi WCF jest dostarczany z CardSpace dostawcę tokenów.</span><span class="sxs-lookup"><span data-stu-id="07688-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="07688-108">Niestandardowego dostawcy tokenów są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="07688-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="07688-109">Jeśli masz Magazyn poświadczeń, który wbudowanego dostawcy tokenu nie może działać z.</span><span class="sxs-lookup"><span data-stu-id="07688-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="07688-110">Jeśli chcesz udostępnić własny niestandardowy mechanizm przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje, na kiedy klient WCF przy użyciu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="07688-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="07688-111">Jeśli tworzysz niestandardowy token.</span><span class="sxs-lookup"><span data-stu-id="07688-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="07688-112">Niniejszy przykład pokazuje sposób tworzenia niestandardowego dostawcy tokenu, który buforuje tokeny wystawione przez Usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="07688-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="07688-113">Aby podsumować, w przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="07688-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="07688-114">Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="07688-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="07688-115">W jaki sposób wystawione tokeny mogą być buforowane i dostarczane do klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="07688-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="07688-116">Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="07688-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="07688-117">W tym przykładzie składa się z konsoli programu klienckiego (Client.exe), program konsoli usługi tokenu zabezpieczeń (Securitytokenservice.exe) i program konsoli usługi (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="07688-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="07688-118">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="07688-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="07688-119">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="07688-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="07688-120">Klient pobiera zabezpieczeń token z Usługa tokenu zabezpieczającego (STS) i sprawia, że żądań synchronicznych usługi dla operacji matematycznych danego i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="07688-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="07688-121">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="07688-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07688-122">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="07688-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="07688-123">Ten przykład przedstawia przy użyciu umowy ICalculator [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="07688-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="07688-124">Konfiguracji tego powiązania na kliencie jest wyświetlany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07688-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="07688-125">Na `security` elementu `wsFederationHttpBinding`, `mode` wartość Określa tryb zabezpieczeń, którym powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="07688-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="07688-126">W tym przykładzie zabezpieczeń wiadomości jest używany, co jest dlaczego `message` elementu `wsFederationHttpBinding` jest określona wewnątrz `security` elementu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="07688-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="07688-127">`issuer` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i powiązanie dla usługi tokenu zabezpieczającego, która wystawia token zabezpieczający do klienta, tak aby klient mógł uwierzytelniać się w kalkulatorze Usługa.</span><span class="sxs-lookup"><span data-stu-id="07688-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="07688-128">Konfiguracji tego powiązania usługi przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07688-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="07688-129">Na `security` elementu `wsFederationHttpBinding`, `mode` wartość Określa tryb zabezpieczeń, którym powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="07688-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="07688-130">W tym przykładzie zabezpieczeń wiadomości jest używany, co jest dlaczego `message` elementu `wsFederationHttpBinding` jest określona wewnątrz `security` elementu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="07688-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="07688-131">`issuerMetadata` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i tożsamości dla punktu końcowego, który może służyć do pobierania metadanych dla usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="07688-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="07688-132">Zachowanie usługi przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07688-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="07688-133">`issuedTokenAuthentication` Element wewnątrz `serviceCredentials` element umożliwia usłudze określanie ograniczeń na tokeny zezwala na klientów przedstawić podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="07688-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="07688-134">Ta konfiguracja Określa, że tokeny podpisane przy użyciu certyfikatu, którego nazwa podmiotu jest CN = usługi STS są akceptowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="07688-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="07688-135">Usługa tokenu zabezpieczającego przedstawia jeden punkt końcowy przy użyciu standardowych wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="07688-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="07688-136">Usługa tokenu zabezpieczającego odpowiada na żądania od klientów tokenów, a pod warunkiem klient jest uwierzytelniany przy użyciu konta Windows, wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia w wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="07688-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="07688-137">Jako część tworzenia tokenu, znaki usługę tokenu zabezpieczającego tokenu przy użyciu klucza prywatnego skojarzonego z CN = certyfikatu usługi STS.</span><span class="sxs-lookup"><span data-stu-id="07688-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="07688-138">Ponadto tworzy klucz symetryczny i szyfruje za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat.</span><span class="sxs-lookup"><span data-stu-id="07688-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="07688-139">Zwracany token do klienta, w usługę tokenu zabezpieczającego zwraca klucz symetryczny.</span><span class="sxs-lookup"><span data-stu-id="07688-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="07688-140">Klient przedstawia wystawiony token usługi Kalkulator i upoważnienie wie klucz symetryczny, tworząc wiadomości za pomocą tego klucza.</span><span class="sxs-lookup"><span data-stu-id="07688-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="07688-141">Poświadczenia klienta oraz dostawcy tokenu</span><span class="sxs-lookup"><span data-stu-id="07688-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="07688-142">Poniższe kroki pokazują jak utworzyć niestandardowego dostawcę tokenów, pamięci podręcznych wystawionych tokenów i zintegrować ją z usługą WCF: zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="07688-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="07688-143">Tworzenie niestandardowego dostawcy tokenów</span><span class="sxs-lookup"><span data-stu-id="07688-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="07688-144">Pisania niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="07688-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="07688-145">Przykład implementuje niestandardowego dostawcę tokenów, który zwraca token zabezpieczający pobrane z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="07688-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="07688-146">Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenów <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="07688-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="07688-147">Ta metoda próbuje pobrać tokenu z pamięci podręcznej, lub Jeśli token nie zostanie znaleziony w pamięci podręcznej, pobiera token z źródłowego dostawcy, a następnie buforuje tego tokenu.</span><span class="sxs-lookup"><span data-stu-id="07688-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="07688-148">W obu przypadkach metoda zwraca `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="07688-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```  
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
  
2. <span data-ttu-id="07688-149">Napisz Menedżer tokenów zabezpieczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="07688-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="07688-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla określonego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="07688-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="07688-151">Menedżer tokenów zabezpieczeń umożliwia również tworzenie wystawców uwierzytelnienia tokenu i serializatorów tokenu, ale te nie są objęte tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="07688-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="07688-152">W tym przykładzie Menedżer tokenów zabezpieczeń niestandardowe dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądana jest metoda, aby zwrócić niestandardowego dostawcy tokenów gdy przekazany wymagania tokenu wskazują, że wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="07688-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```  
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
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="07688-153">Wpisz poświadczenia niestandardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="07688-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="07688-154">Klasa poświadczeń klienta jest używany do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy bezpieczeństwo Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatory.</span><span class="sxs-lookup"><span data-stu-id="07688-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
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
        Get  
        {  
          return this.cache;  
        }  
        Set  
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
  
4. <span data-ttu-id="07688-155">Implementowanie pamięci podręcznej tokenu.</span><span class="sxs-lookup"><span data-stu-id="07688-155">Implement the token cache.</span></span> <span data-ttu-id="07688-156">W przykładowej implementacji użyto abstrakcyjna klasa bazowa, za pomocą którego odbiorców tokenu pamięć podręczna wchodzić w interakcje z pamięcią podręczną.</span><span class="sxs-lookup"><span data-stu-id="07688-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="07688-157">Klienta można użyć poświadczeń klienta niestandardowe przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="07688-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="07688-158">Działa aplikacja przykładowa</span><span class="sxs-lookup"><span data-stu-id="07688-158">Running the sample</span></span>  
 <span data-ttu-id="07688-159">Zobacz następujące instrukcje do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="07688-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="07688-160">Po uruchomieniu przykładu, żądania tokenu zabezpieczeń są wyświetlane w oknie konsoli usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="07688-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="07688-161">Operacja żądania i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="07688-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="07688-162">Naciśnij klawisz ENTER w żadnym z okna konsoli do zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07688-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="07688-163">Plik wsadowy plik Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="07688-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="07688-164">Plik wsadowy plik Setup.cmd, które są dołączone do tego przykładu umożliwia skonfigurowanie serwera i Usługa tokenu zabezpieczającego z certyfikatami odpowiednie do uruchamiania aplikacji samodzielnie hostowany.</span><span class="sxs-lookup"><span data-stu-id="07688-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="07688-165">Plik wsadowy tworzy dwa certyfikaty, że zarówno w CurrentUser/TrustedPeople magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="07688-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="07688-166">Pierwszy certyfikat ma nazwę podmiotu, CN = usługi STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które generuje dla klienta.</span><span class="sxs-lookup"><span data-stu-id="07688-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="07688-167">Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę tokenu zabezpieczającego do szyfrowania klucza tajnego, dzięki czemu usługa może go odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="07688-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07688-168">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="07688-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="07688-169">Uruchom plik Setup.cmd plik do tworzenia wymaganych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="07688-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="07688-170">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07688-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="07688-171">Upewnij się, że wszystkie projekty w rozwiązaniu są kompilowane (udostępnione, RSTRSTR, usługi, SecurityTokenService i klienta).</span><span class="sxs-lookup"><span data-stu-id="07688-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="07688-172">Upewnij się, że Service.exe i SecurityTokenService.exe są uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="07688-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="07688-173">Uruchom Client.exe.</span><span class="sxs-lookup"><span data-stu-id="07688-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="07688-174">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="07688-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="07688-175">Uruchom Cleanup.cmd w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="07688-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07688-176">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="07688-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07688-177">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="07688-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07688-178">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="07688-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07688-179">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="07688-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
