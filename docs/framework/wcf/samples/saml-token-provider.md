---
title: Dostawca tokenów SAML
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 87aef572c2179034d295361c62942cea2ad6ed7a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424236"
---
# <a name="saml-token-provider"></a><span data-ttu-id="43dad-102">Dostawca tokenów SAML</span><span class="sxs-lookup"><span data-stu-id="43dad-102">SAML Token Provider</span></span>
<span data-ttu-id="43dad-103">Ten przykład pokazuje, jak zaimplementować niestandardowego dostawcę tokenów SAML klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="43dad-104">Dostawca tokenu w Windows Communication Foundation (WCF) służy do dostarczania poświadczeń do infrastruktury zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="43dad-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="43dad-105">Dostawca tokenu ogólnie bada cel i wystawia odpowiednie poświadczenia, aby infrastruktura zabezpieczeń mogła zabezpieczyć komunikat.</span><span class="sxs-lookup"><span data-stu-id="43dad-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="43dad-106">Usługa WCF jest dostarczana z domyślnym dostawcą tokenu Menedżera poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="43dad-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="43dad-107">Usługa WCF jest również dostarczana z dostawcą tokenu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="43dad-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="43dad-108">Dostawcy tokenów niestandardowych są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="43dad-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="43dad-109">Jeśli masz magazyn poświadczeń, którego nie mogą używać dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="43dad-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="43dad-110">Jeśli chcesz zapewnić własny niestandardowy mechanizm przekształcania poświadczeń z punktu, gdy użytkownik poda szczegółowe informacje o tym, kiedy struktura klienta programu WCF używa tych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="43dad-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="43dad-111">W przypadku kompilowania niestandardowego tokenu.</span><span class="sxs-lookup"><span data-stu-id="43dad-111">If you are building a custom token.</span></span>

 <span data-ttu-id="43dad-112">Ten przykład pokazuje, jak utworzyć niestandardowego dostawcę tokenów, który umożliwia użycie tokenu SAML uzyskanego spoza struktury klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="43dad-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="43dad-113">Podsumowując, ten przykład ilustruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="43dad-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="43dad-114">Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="43dad-114">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="43dad-115">Jak można przesłać token SAML do niestandardowych poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-115">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="43dad-116">Jak token SAML jest dostarczany do struktury klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="43dad-116">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="43dad-117">Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X. 509 serwera.</span><span class="sxs-lookup"><span data-stu-id="43dad-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="43dad-118">Usługa udostępnia dwa punkty końcowe do komunikacji z usługą, zdefiniowane przy użyciu pliku konfiguracji App. config. Każdy punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="43dad-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="43dad-119">Powiązanie jest skonfigurowane przy użyciu standardowego `wsFederationHttpBinding`, który używa zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43dad-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="43dad-120">Jeden z punktów końcowych oczekuje, że klient uwierzytelnia się za pomocą tokenu SAML, który używa symetrycznego klucza testowego, podczas gdy drugi oczekuje, że klient uwierzytelnia się za pomocą tokenu SAML, który używa klucza nieasymetrycznego dowodu.</span><span class="sxs-lookup"><span data-stu-id="43dad-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="43dad-121">Usługa konfiguruje również certyfikat usługi przy użyciu zachowania `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="43dad-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="43dad-122">Zachowanie `serviceCredentials` pozwala konfigurować certyfikat usługi.</span><span class="sxs-lookup"><span data-stu-id="43dad-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="43dad-123">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewniania ochrony komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43dad-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="43dad-124">Następująca konfiguracja odwołuje się do certyfikatu "localhost" zainstalowanego podczas konfiguracji przykładowej zgodnie z opisem w instrukcji konfiguracyjnych na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="43dad-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="43dad-125">Zachowanie `serviceCredentials` pozwala także skonfigurować certyfikaty, które są zaufane do podpisywania tokenów SAML.</span><span class="sxs-lookup"><span data-stu-id="43dad-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="43dad-126">Następująca konfiguracja odwołuje się do certyfikatu "Alicja" zainstalowanego podczas próby.</span><span class="sxs-lookup"><span data-stu-id="43dad-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="43dad-127">Poniższe kroki pokazują, jak opracować niestandardowego dostawcę tokenów SAML i zintegrować go z WCF: Framework zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="43dad-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="43dad-128">Napisz niestandardowego dostawcę tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="43dad-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="43dad-129">Przykład implementuje niestandardowego dostawcę tokenów SAML, który zwraca token zabezpieczający na podstawie potwierdzenia SAML dostarczonego w czasie konstruowania.</span><span class="sxs-lookup"><span data-stu-id="43dad-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="43dad-130">Aby wykonać to zadanie, dostawca niestandardowego tokenu pochodzi od klasy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> i zastępuje metodę <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="43dad-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="43dad-131">Ta metoda tworzy i zwraca nowe `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="43dad-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="43dad-132">Napisz niestandardowego menedżera tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="43dad-132">Write custom security token manager.</span></span>

     <span data-ttu-id="43dad-133">Klasa <xref:System.IdentityModel.Selectors.SecurityTokenManager> służy do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla konkretnych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, które są do niego przesyłane w metodzie `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="43dad-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="43dad-134">Menedżer tokenów zabezpieczających jest również używany do tworzenia wystawców tokenów i serializatorów tokenów, ale nie są one objęte tym przykładem.</span><span class="sxs-lookup"><span data-stu-id="43dad-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="43dad-135">W tym przykładzie niestandardowy Menedżer tokenów zabezpieczających dziedziczy z klasy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> i zastępuje metodę `CreateSecurityTokenProvider`, aby zwracała niestandardowego dostawcę tokenów SAML, gdy spełnione wymagania dotyczące tokenu wskazują, że zażądano tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="43dad-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="43dad-136">Jeśli Klasa poświadczeń klienta (zobacz krok 3) nie określiła potwierdzenia, Menedżer tokenów zabezpieczających tworzy odpowiednie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="43dad-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```csharp
    public class SamlSecurityTokenManager :
     ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="43dad-137">Napisz niestandardowe poświadczenie klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-137">Write a custom client credential.</span></span>

     <span data-ttu-id="43dad-138">Klasa poświadczeń klienta służy do reprezentowania poświadczeń skonfigurowanych dla serwera proxy klienta i tworzy Menedżera tokenów zabezpieczających, który służy do uzyskiwania wystawców tokenów, dostawców tokenów i serializatorów tokenów.</span><span class="sxs-lookup"><span data-stu-id="43dad-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="43dad-139">Skonfiguruj klienta tak, aby korzystał z niestandardowego poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="43dad-140">Przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta, aby klient mógł użyć niestandardowego poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="43dad-141">W usłudze są wyświetlane oświadczenia skojarzone z obiektem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="43dad-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="43dad-142">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="43dad-143">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="43dad-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="43dad-144">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43dad-144">Setup Batch File</span></span>
 <span data-ttu-id="43dad-145">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednim certyfikatem w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="43dad-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="43dad-146">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="43dad-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="43dad-147">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43dad-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="43dad-148">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="43dad-148">Creating the server certificate:</span></span>

     <span data-ttu-id="43dad-149">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="43dad-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="43dad-150">Zmienna `%SERVER_NAME%` określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="43dad-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="43dad-151">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="43dad-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="43dad-152">Wartość domyślna w tym pliku wsadowym to localhost.</span><span class="sxs-lookup"><span data-stu-id="43dad-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="43dad-153">Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="43dad-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="43dad-154">Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="43dad-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="43dad-155">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="43dad-156">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="43dad-157">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="43dad-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="43dad-158">Tworzenie certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="43dad-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="43dad-159">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat wystawcy, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="43dad-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="43dad-160">Zmienna `%USER_NAME%` określa nazwę wystawcy.</span><span class="sxs-lookup"><span data-stu-id="43dad-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="43dad-161">Zmień tę zmienną, aby określić własną nazwę wystawcy.</span><span class="sxs-lookup"><span data-stu-id="43dad-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="43dad-162">Wartość domyślna w tym pliku wsadowym to Alicja.</span><span class="sxs-lookup"><span data-stu-id="43dad-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="43dad-163">Certyfikat jest przechowywany w magazynie w lokalizacji magazynu CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="43dad-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="43dad-164">Instalowanie certyfikatu wystawcy w zaufanym magazynie certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="43dad-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="43dad-165">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="43dad-166">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="43dad-167">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów serwera z certyfikatem wystawcy nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="43dad-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="43dad-168">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="43dad-168">To set up and build the sample</span></span>

1. <span data-ttu-id="43dad-169">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43dad-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="43dad-170">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43dad-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="43dad-171">Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="43dad-172">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="43dad-172">To run the sample on the same computer</span></span>

1. <span data-ttu-id="43dad-173">Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="43dad-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="43dad-174">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="43dad-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="43dad-175">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="43dad-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="43dad-176">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="43dad-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="43dad-177">Uruchom usługę Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="43dad-177">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="43dad-178">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="43dad-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="43dad-179">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-179">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="43dad-180">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="43dad-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="43dad-181">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="43dad-181">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="43dad-182">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="43dad-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="43dad-183">Skopiuj pliki programu Service Files do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="43dad-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="43dad-184">Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="43dad-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="43dad-185">Musisz mieć certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="43dad-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="43dad-186">Plik Service. exe. config musi zostać zaktualizowany w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="43dad-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="43dad-187">Można utworzyć certyfikat serwera, modyfikując plik wsadowy Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="43dad-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="43dad-188">Należy pamiętać, że plik Setup. bat musi być uruchamiany wiersz polecenia dla deweloperów w otwartym oknie programu Visual Studio z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="43dad-188">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="43dad-189">Należy ustawić zmienną `%SERVER_NAME%` na w pełni kwalifikowaną nazwę hosta komputera, który jest używany do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="43dad-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="43dad-190">Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="43dad-191">Ten krok nie jest konieczny, gdy certyfikat serwera jest wystawiony przez zaufanego wystawcy klienta.</span><span class="sxs-lookup"><span data-stu-id="43dad-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="43dad-192">W pliku Service. exe. config na komputerze usługi Zmień wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="43dad-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="43dad-193">Na komputerze usługi Uruchom program Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="43dad-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="43dad-194">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="43dad-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="43dad-195">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="43dad-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="43dad-196">Na komputerze klienckim uruchom `Client.exe` z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="43dad-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="43dad-197">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="43dad-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="43dad-198">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="43dad-198">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="43dad-199">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="43dad-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
