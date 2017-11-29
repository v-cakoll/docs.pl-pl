---
title: "Niezawodny dostawca wystawionych tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d7b4fdde1d231f90b0d7f78e11046312c65a859
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="f34ee-102">Niezawodny dostawca wystawionych tokenów</span><span class="sxs-lookup"><span data-stu-id="f34ee-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="f34ee-103">W tym przykładzie pokazano, jak do zaimplementowania niestandardowego klienta, dostawca wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="f34ee-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="f34ee-104">Omówienie</span><span class="sxs-lookup"><span data-stu-id="f34ee-104">Discussion</span></span>  
 <span data-ttu-id="f34ee-105">Dostawca tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] umożliwia podanie poświadczeń w celu zabezpieczenia infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f34ee-105">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="f34ee-106">Dostawca tokenu ogólnie sprawdza obiektu docelowego i problemów odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f34ee-107">jest dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-107"> ships with a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="f34ee-108">Tokenów niestandardowi są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="f34ee-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="f34ee-109">Jeśli masz Magazyn poświadczeń, które wbudowanego dostawcy tokenów nie może pracować z.</span><span class="sxs-lookup"><span data-stu-id="f34ee-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
-   <span data-ttu-id="f34ee-110">Jeśli chcesz udostępnić własny niestandardowy mechanizm do przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje o tym, kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta używa poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="f34ee-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses the credentials.</span></span>  
  
-   <span data-ttu-id="f34ee-111">Jeśli tworzysz niestandardowy token.</span><span class="sxs-lookup"><span data-stu-id="f34ee-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="f34ee-112">Ten przykład przedstawia sposób tworzenia niestandardowego dostawcę tokenów, który buforuje tokenów wystawionych przez zabezpieczenia tokenu usługi (STS).</span><span class="sxs-lookup"><span data-stu-id="f34ee-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="f34ee-113">Krótko mówiąc, w tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="f34ee-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="f34ee-114">Jak można skonfigurować klienta z niestandardowego dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="f34ee-115">Jak wystawione tokeny mogą być buforowane i przekazane do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="f34ee-115">How issued tokens can be cached and provided to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
-   <span data-ttu-id="f34ee-116">Jak serwer jest uwierzytelniany przez klienta przy użyciu certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="f34ee-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="f34ee-117">W tym przykładzie składa się z konsoli programu klienckiego (Client.exe), program konsoli usługi tokenu zabezpieczeń (Securitytokenservice.exe) i program konsoli usługi (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="f34ee-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="f34ee-118">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="f34ee-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="f34ee-119">Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="f34ee-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="f34ee-120">Klient pobiera zabezpieczeń token z zabezpieczeń usługi tokenów (STS) i zgłasza żądania dotyczące synchroniczne usługi dla operacji matematycznych danego i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="f34ee-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="f34ee-121">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="f34ee-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f34ee-122">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f34ee-123">Ten przykład przedstawia, za pomocą kontraktu ICalculator [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f34ee-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="f34ee-124">W poniższym kodzie przedstawiono konfiguracji tego powiązania na kliencie.</span><span class="sxs-lookup"><span data-stu-id="f34ee-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="f34ee-125">Na `security` elementu `wsFederationHttpBinding`, `mode` wartość konfiguruje tryb zabezpieczeń, którym powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="f34ee-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="f34ee-126">W tym przykładzie zabezpieczeń wiadomości jest używany, która jest dlaczego `message` elementu `wsFederationHttpBinding` określono wewnątrz `security` elementu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f34ee-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="f34ee-127">`issuer` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i powiązanie dla usługi tokenu zabezpieczającego, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnić się Kalkulator Usługa.</span><span class="sxs-lookup"><span data-stu-id="f34ee-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="f34ee-128">Konfiguracji tego powiązania usługi przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f34ee-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="f34ee-129">Na `security` elementu `wsFederationHttpBinding`, `mode` wartość konfiguruje tryb zabezpieczeń, którym powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="f34ee-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="f34ee-130">W tym przykładzie zabezpieczeń wiadomości jest używany, która jest dlaczego `message` elementu `wsFederationHttpBinding` określono wewnątrz `security` elementu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f34ee-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="f34ee-131">`issuerMetadata` Elementu `wsFederationHttpBinding` wewnątrz `message` elementu `wsFederationHttpBinding` Określa adres i tożsamości dla punktu końcowego, który może służyć do pobierania metadanych dla usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="f34ee-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="f34ee-132">Zachowanie usługi przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f34ee-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="f34ee-133">`issuedTokenAuthentication` Element wewnątrz `serviceCredentials` element umożliwia usługę, aby określić ograniczeń na tokeny umożliwia klientom prezentować podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f34ee-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="f34ee-134">Ta konfiguracja Określa, że tokeny podpisane za pomocą certyfikatu, którego podmiot jest CN = STS są akceptowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="f34ee-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="f34ee-135">Usługa tokenu zabezpieczającego przedstawia przy użyciu standardowych wsHttpBinding jeden punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f34ee-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="f34ee-136">Usługi tokenu zabezpieczającego odpowiada na żądania od klientów tokenów i pod warunkiem klienta jest uwierzytelniany przy użyciu konta systemu Windows, wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia w wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="f34ee-137">Podczas tworzenia tokenu znaki usługi tokenu zabezpieczeń tokenu przy użyciu klucza prywatnego skojarzonego z CN = certyfikat STS.</span><span class="sxs-lookup"><span data-stu-id="f34ee-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="f34ee-138">Ponadto tworzy klucza symetrycznego i szyfruje go za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat.</span><span class="sxs-lookup"><span data-stu-id="f34ee-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="f34ee-139">Zwracany token do klienta, usługę tokenu zabezpieczającego zwraca klucz symetryczny.</span><span class="sxs-lookup"><span data-stu-id="f34ee-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="f34ee-140">Klient prezentuje wystawionego tokenu z usługą Kalkulator i okaże się wie klucza symetrycznego, tworząc wiadomości z tego klucza.</span><span class="sxs-lookup"><span data-stu-id="f34ee-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="f34ee-141">Niestandardowe poświadczenia i dostawcy tokenów</span><span class="sxs-lookup"><span data-stu-id="f34ee-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="f34ee-142">Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenów, że pamięci podręcznych wystawionych tokenów i ich integracji z programem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f34ee-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="f34ee-143">Aby utworzyć niestandardowego dostawcę tokenów</span><span class="sxs-lookup"><span data-stu-id="f34ee-143">To develop a custom token provider</span></span>  
  
1.  <span data-ttu-id="f34ee-144">Pisanie niestandardowych dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="f34ee-145">Przykład implementuje niestandardowego dostawcę tokenów, który zwraca token zabezpieczający pobierane z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f34ee-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="f34ee-146">Aby wykonać to zadanie, pochodzi niestandardowego dostawcy tokenu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f34ee-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="f34ee-147">Ta metoda próbuje pobrać tokenu z pamięci podręcznej, lub Jeśli token nie można znaleźć w pamięci podręcznej, pobiera token z podstawowym dostawcy, a następnie buforuje tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="f34ee-148">W obu przypadkach metoda zwraca `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="f34ee-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="f34ee-149">Zapis Menedżer tokenów zabezpieczających niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f34ee-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="f34ee-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla określonego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="f34ee-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="f34ee-151">Menedżer tokenów zabezpieczających jest również używane do utworzenia wystawcy uwierzytelnienia tokenu i serializatorów tokenu, ale te nie są objęte w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f34ee-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="f34ee-152">W tym przykładzie Menedżer tokenów zabezpieczających niestandardowych dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądanej metody do zwracania niestandardowego dostawcy tokenu podczas przekazany wymagania tokenu wskazują, że wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
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
  
3.  <span data-ttu-id="f34ee-153">Wpisz poświadczenia niestandardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f34ee-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="f34ee-154">Klasa poświadczeń klienta jest używana do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i serializatorów tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f34ee-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
4.  <span data-ttu-id="f34ee-155">Implementuje pamięci podręcznej tokenu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-155">Implement the token cache.</span></span> <span data-ttu-id="f34ee-156">Przykładowe zastosowanie używa abstrakcyjna klasa podstawowa, za pomocą którego interakcji użytkowników danego pamięci podręcznej tokenu z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f34ee-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="f34ee-157">Dla klienta do używania poświadczeń klienta niestandardowych próbka usuwa domyślną klasę poświadczeń klienta i udostępnia nową klasę poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="f34ee-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="f34ee-158">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="f34ee-158">Running the sample</span></span>  
 <span data-ttu-id="f34ee-159">Zobacz poniższe instrukcje do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="f34ee-160">Po uruchomieniu próbki żądania tokenu zabezpieczającego jest wyświetlany w oknie konsoli usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="f34ee-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="f34ee-161">Operacja żądania i odpowiedzi są wyświetlane w oknie konsoli klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="f34ee-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="f34ee-162">Naciśnij klawisz ENTER w żadnym z okna konsoli można zamknąć aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f34ee-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="f34ee-163">Plik wsadowy Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="f34ee-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="f34ee-164">Plik wsadowy Setup.cmd uwzględnionych w tym przykładzie umożliwia skonfigurowanie serwera i usługi tokenu zabezpieczającego z odpowiednich certyfikatów do uruchomienia aplikacji siebie.</span><span class="sxs-lookup"><span data-stu-id="f34ee-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="f34ee-165">Plik wsadowy tworzy dwa certyfikaty zarówno w CurrentUser/TrustedPeople magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="f34ee-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="f34ee-166">Pierwszy certyfikat ma nazwę podmiotu, CN = STS i jest używany przez usługę tokenu zabezpieczającego do podpisywania tokenów zabezpieczających, które wystawia klientowi.</span><span class="sxs-lookup"><span data-stu-id="f34ee-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="f34ee-167">Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę tokenu zabezpieczającego można zaszyfrować klucza tajnego, aby można go odszyfrować usługi.</span><span class="sxs-lookup"><span data-stu-id="f34ee-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f34ee-168">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="f34ee-168">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f34ee-169">Uruchom plik Setup.cmd do tworzenia wymaganych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="f34ee-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2.  <span data-ttu-id="f34ee-170">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f34ee-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="f34ee-171">Upewnij się, że skompilowano wszystkie projekty w rozwiązaniu (Shared, RSTRSTR usługi, SecurityTokenService i klienta).</span><span class="sxs-lookup"><span data-stu-id="f34ee-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3.  <span data-ttu-id="f34ee-172">Upewnij się, że Service.exe i SecurityTokenService.exe są uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="f34ee-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="f34ee-173">Uruchom Client.exe.</span><span class="sxs-lookup"><span data-stu-id="f34ee-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f34ee-174">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="f34ee-174">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="f34ee-175">Uruchamianie Cleanup.cmd w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="f34ee-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f34ee-176">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f34ee-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f34ee-177">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f34ee-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f34ee-178">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="f34ee-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f34ee-179">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f34ee-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a><span data-ttu-id="f34ee-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f34ee-180">See Also</span></span>
