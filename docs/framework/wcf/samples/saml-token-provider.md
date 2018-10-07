---
title: Dostawca tokenów SAML
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: dfd693e262e7566c865d5b9faed5b9e00a8cfec9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845323"
---
# <a name="saml-token-provider"></a><span data-ttu-id="bb4d5-102">Dostawca tokenów SAML</span><span class="sxs-lookup"><span data-stu-id="bb4d5-102">SAML Token Provider</span></span>
<span data-ttu-id="bb4d5-103">Ten przykład demonstruje sposób implementacji niestandardowego klienta Dostawca tokenów SAML.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="bb4d5-104">Dostawca tokenu w Windows Communication Foundation (WCF) jest używany dla podanie poświadczeń w celu infrastruktura zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="bb4d5-105">Dostawcy tokenu, który sprawdza ogólnie rzecz biorąc, element docelowy i problemy odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="bb4d5-106">Usługi WCF jest dostarczany z domyślny dostawca tokenu Menedżera poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="bb4d5-107">Usługi WCF jest również dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="bb4d5-108">Niestandardowego dostawcy tokenów są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="bb4d5-108">Custom token providers are useful in the following cases:</span></span>

-   <span data-ttu-id="bb4d5-109">Jeśli masz Magazyn poświadczeń, który te dostawcy tokenów nie może działać z.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-109">If you have a credential store that these token providers cannot operate with.</span></span>

-   <span data-ttu-id="bb4d5-110">Jeśli chcesz udostępnić własny niestandardowy mechanizm przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje, na kiedy struktura klienta WCF przy użyciu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

-   <span data-ttu-id="bb4d5-111">Jeśli tworzysz niestandardowy token.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-111">If you are building a custom token.</span></span>

 <span data-ttu-id="bb4d5-112">Niniejszy przykład pokazuje sposób tworzenia niestandardowego dostawcę tokenów, który umożliwia tokenu SAML uzyskany z poza szablonem klienta WCF, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="bb4d5-113">Aby podsumować, w przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="bb4d5-113">To summarize, this sample demonstrates the following:</span></span>

-   <span data-ttu-id="bb4d5-114">Jak można skonfigurować klienta przy użyciu niestandardowego dostawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-114">How a client can be configured with a custom token provider.</span></span>

-   <span data-ttu-id="bb4d5-115">Jak tokenu SAML mogą być przekazywane poświadczenia niestandardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-115">How a SAML token can be passed to the custom client credentials.</span></span>

-   <span data-ttu-id="bb4d5-116">Jak struktura klienta programu WCF zapewnia SAML token.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-116">How the SAML token is provided to the WCF client framework.</span></span>

-   <span data-ttu-id="bb4d5-117">Jak serwer jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="bb4d5-118">Usługa udostępnia dwa punkty końcowe dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="bb4d5-119">Powiązanie jest skonfigurowane przy użyciu standardowego `wsFederationHttpBinding`, która używa zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="bb4d5-120">Jeden punkt końcowy oczekuje klienta do uwierzytelniania za pomocą tokenu SAML, które używa klucza symetrycznego dowód, podczas gdy druga oczekuje klienta do uwierzytelniania przy użyciu tokenu SAML, która używa klucza asymetrycznego dowód.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="bb4d5-121">Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="bb4d5-122">`serviceCredentials` Zachowanie umożliwia skonfigurowanie certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="bb4d5-123">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi, a także zapewnienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="bb4d5-124">Następująca konfiguracja odwołuje się do certyfikatu "localhost" zainstalowany podczas instalacji przykładowej zgodnie z opisem w instrukcje instalacji, na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="bb4d5-125">`serviceCredentials` Zachowanie umożliwia również konfigurowanie certyfikatów, które są zaufane, aby zarejestrować tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="bb4d5-126">Następująca konfiguracja odwołuje się do certyfikatu "Alicja" instalowane w ramach przykładu.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

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

 <span data-ttu-id="bb4d5-127">Poniższe kroki pokazują jak utworzyć niestandardowy Dostawca tokenów SAML i zintegrować ją z usługą WCF: struktury zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="bb4d5-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1.  <span data-ttu-id="bb4d5-128">Napisać niestandardowy Dostawca tokenów SAML.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="bb4d5-129">Przykład implementuje niestandardowy Dostawca tokenów SAML, która zwraca token zabezpieczający, w oparciu o potwierdzenie SAML, który znajduje się w czasie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="bb4d5-130">Aby wykonać to zadanie, niestandardowego dostawcy tokenów jest tworzony na podstawie <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="bb4d5-131">Ta metoda tworzy i zwraca nowy `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```
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

2.  <span data-ttu-id="bb4d5-132">Napisz Menedżer tokenów zabezpieczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-132">Write custom security token manager.</span></span>

     <span data-ttu-id="bb4d5-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Klasa jest używana do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> dla konkretnego <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="bb4d5-134">Menedżer tokenów zabezpieczeń jest również używany do tworzenia wystawcy uwierzytelnienia tokenu i Serializator tokenów, ale te nie są objęte tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="bb4d5-135">W tym przykładowe niestandardowe zabezpieczeń, Menedżer tokenów dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądana jest metoda do zwrócenia niestandardowego dostawcy tokenów SAML przy przekazany wymagania tokenu wskazują, że SAML token.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="bb4d5-136">Jeśli klasa poświadczeń klienta nie (zobacz krok 3) określił potwierdzenie, Menedżer tokenów zabezpieczeń tworzy odpowiednie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```
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

3.  <span data-ttu-id="bb4d5-137">Wpisz poświadczenia niestandardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-137">Write a custom client credential.</span></span>

     <span data-ttu-id="bb4d5-138">Klasa poświadczeń klienta jest używany do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy zabezpieczeń Menedżer tokenów, który jest używany do uzyskiwania wystawców uwierzytelnienia tokenu, dostawcy tokenów i tokenów serializatora.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```
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

4.  <span data-ttu-id="bb4d5-139">Konfigurowanie klienta do używania poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="bb4d5-140">Przykład usuwa domyślną klasę poświadczeń klienta i dostarcza nową klasę poświadczeń klienta, dzięki czemu klient może używać poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```
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

 <span data-ttu-id="bb4d5-141">W usłudze są wyświetlane oświadczenia skojarzone z funkcją wywołującą.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="bb4d5-142">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bb4d5-143">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="bb4d5-144">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="bb4d5-144">Setup Batch File</span></span>
 <span data-ttu-id="bb4d5-145">Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera z odpowiedni certyfikat, aby uruchomić samodzielnie hostowanej aplikacji, która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="bb4d5-146">Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="bb4d5-147">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

-   <span data-ttu-id="bb4d5-148">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="bb4d5-148">Creating the server certificate:</span></span>

     <span data-ttu-id="bb4d5-149">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="bb4d5-150">`%SERVER_NAME%` Zmienna Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="bb4d5-151">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="bb4d5-152">Wartość domyślna, w tym pliku wsadowego to localhost.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="bb4d5-153">Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="bb4d5-154">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="bb4d5-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="bb4d5-155">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="bb4d5-156">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="bb4d5-157">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

-   <span data-ttu-id="bb4d5-158">Tworzenie certyfikatu wystawcy.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="bb4d5-159">Następujące wiersze z pliku wsadowego Setup.bat Utwórz certyfikat wystawca ma być używany.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="bb4d5-160">`%USER_NAME%` Zmiennej określa nazwę wystawcy.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="bb4d5-161">Zmień tę wartość, aby określić nazwę wystawcy.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="bb4d5-162">Wartość domyślna, w tym pliku wsadowego to Alicji.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="bb4d5-163">Certyfikat jest przechowywany w magazynie użytkownika znajdujące się w lokalizacji magazynu CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="bb4d5-164">Instalowanie certyfikatu wystawcy do magazynu zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="bb4d5-165">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="bb4d5-166">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="bb4d5-167">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów serwera za pomocą certyfikatu wystawcy nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="bb4d5-168">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="bb4d5-168">To set up and build the sample</span></span>

1.  <span data-ttu-id="bb4d5-169">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bb4d5-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="bb4d5-170">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bb4d5-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="bb4d5-171">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="bb4d5-172">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="bb4d5-172">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="bb4d5-173">Uruchom Setup.bat z folderu instalacji przykładowej w wierszu polecenia programu Visual Studio 2012 uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="bb4d5-174">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="bb4d5-175">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="bb4d5-176">Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="bb4d5-177">Uruchom Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="bb4d5-178">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="bb4d5-179">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="bb4d5-180">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bb4d5-180">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bb4d5-181">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="bb4d5-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="bb4d5-182">Utwórz katalog na komputerze usługi, aby pliki binarne usługi.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="bb4d5-183">Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="bb4d5-184">Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="bb4d5-185">Musi mieć certyfikat serwera o nazwie podmiotu, który zawiera w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="bb4d5-186">Plik Service.exe.config należy zaktualizować w celu odzwierciedlenia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="bb4d5-187">Można utworzyć certyfikatu serwera, modyfikując plik wsadowy Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="bb4d5-188">Należy pamiętać, że plik Setup.bat jest musi zostać uruchomiony w oknie wiersza polecenia programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="bb4d5-189">Należy ustawić `%SERVER_NAME%` zmiennej do w pełni kwalifikowany host nazwę komputera, na którym jest używana do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="bb4d5-190">Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="bb4d5-191">Ten krok nie jest konieczne, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="bb4d5-192">W pliku Service.exe.config na komputerze usługi Zmień wartość z adresu podstawowego, aby określić nazwę komputera w pełni kwalifikowaną, zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="bb4d5-193">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="bb4d5-194">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="bb4d5-195">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="bb4d5-196">Na komputerze klienckim, należy uruchomić `Client.exe` z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="bb4d5-197">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bb4d5-197">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="bb4d5-198">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="bb4d5-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="bb4d5-199">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="bb4d5-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb4d5-200">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb4d5-200">See Also</span></span>
