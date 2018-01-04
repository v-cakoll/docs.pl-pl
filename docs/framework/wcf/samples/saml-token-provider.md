---
title: "Dostawca tokenów SAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7afdbcde68a811dd8fb2be84c1ae298496992c9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="saml-token-provider"></a><span data-ttu-id="7a6ae-102">Dostawca tokenów SAML</span><span class="sxs-lookup"><span data-stu-id="7a6ae-102">SAML Token Provider</span></span>
<span data-ttu-id="7a6ae-103">W tym przykładzie pokazano, jak implementacja klienta niestandardowego dostawcy tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="7a6ae-104">Dostawca tokenu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do podawania poświadczeń w celu zabezpieczenia infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="7a6ae-105">Dostawca tokenu ogólnie sprawdza obiektu docelowego i problemów odpowiednie poświadczenia, aby infrastruktura zabezpieczeń można zabezpieczyć komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7a6ae-106">jest dostarczany z domyślnym dostawcy tokenu Menedżera poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-106"> ships with the default Credential Manager Token Provider.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7a6ae-107">również jest dostarczany z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-107"> also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="7a6ae-108">Tokenów niestandardowi są przydatne w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="7a6ae-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="7a6ae-109">Jeśli masz Magazyn poświadczeń, które tych dostawców tokenu nie może pracować z.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="7a6ae-110">Jeśli chcesz udostępnić własny niestandardowy mechanizm do przekształcania poświadczenia z punktu, gdy użytkownik udostępnia szczegółowe informacje o tym, kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta używa poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="7a6ae-111">Jeśli tworzysz niestandardowy token.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="7a6ae-112">Ten przykład przedstawia sposób tworzenia niestandardowego dostawcę tokenów, który umożliwia tokenu SAML uzyskany poza [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta do użycia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework to be used.</span></span>  
  
 <span data-ttu-id="7a6ae-113">Krótko mówiąc, w tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="7a6ae-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="7a6ae-114">Jak można skonfigurować klienta z niestandardowego dostawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="7a6ae-115">Jak tokenu SAML mogą być przekazywane do poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-115">How a SAML token can be passed to the custom client credentials.</span></span>  
  
-   <span data-ttu-id="7a6ae-116">Jak tokenu SAML są dostarczane do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-116">How the SAML token is provided to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework.</span></span>  
  
-   <span data-ttu-id="7a6ae-117">Jak serwer jest uwierzytelniany przez klienta przy użyciu certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="7a6ae-118">Usługa udostępnia dwa punkty końcowe komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Każdy punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7a6ae-119">Powiązanie jest skonfigurowane z normą `wsFederationHttpBinding`, zabezpieczenia komunikatów, który używa.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="7a6ae-120">Jeden punkt końcowy oczekuje klienta do uwierzytelniania za pomocą tokenu SAML, który używa symetrycznego klucza poświadczającego, podczas gdy druga oczekuje klienta do uwierzytelniania za pomocą tokenu SAML, który używa klucza potwierdzającego asymetrycznego.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="7a6ae-121">Usługa konfiguruje również certyfikat usługi przy użyciu `serviceCredentials` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="7a6ae-122">`serviceCredentials` Zachowanie umożliwia konfigurowanie certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="7a6ae-123">Certyfikat usługi jest używany przez klienta do uwierzytelniania usługi i zapewnienia ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="7a6ae-124">Następująca konfiguracja odwołuje się do certyfikatu "localhost" instalowane podczas instalacji próbki zgodnie z opisem w instrukcjach instalacji na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="7a6ae-125">`serviceCredentials` Zachowanie umożliwia również konfigurowanie certyfikatów, które są zaufane do podpisywania tokenów SAML.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="7a6ae-126">Następująca konfiguracja odwołuje się do certyfikatu "Alicja" instalowane w ramach przykładu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>  
  
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
  
 <span data-ttu-id="7a6ae-127">Poniższe kroki pokazują, jak utworzyć niestandardowego dostawcę tokenu SAML i ich integracji z programem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: Struktura zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="7a6ae-127">The following steps show how to develop a custom SAML token provider and integrate it with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: security framework:</span></span>  
  
1.  <span data-ttu-id="7a6ae-128">Pisanie niestandardowych dostawcy tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-128">Write a custom SAML token provider.</span></span>  
  
     <span data-ttu-id="7a6ae-129">Przykład implementuje niestandardowego dostawcę tokenów SAML, który zwraca token zabezpieczający oparte na potwierdzenia języka SAML, dostarczonego w czasie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>  
  
     <span data-ttu-id="7a6ae-130">Aby wykonać to zadanie, niestandardowego dostawcy tokenu jest pochodną <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy i zastąpień <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="7a6ae-131">Ta metoda tworzy i zwraca nowy `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-131">This method creates and returns a new `SecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="7a6ae-132">Zapis Menedżer tokenów zabezpieczających niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-132">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="7a6ae-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Klasa jest używana do tworzenia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> określonych <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> przekazanego do niej w `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="7a6ae-134">Menedżer tokenów zabezpieczających jest również używane do utworzenia wystawcy uwierzytelnienia tokenu i Serializator tokenu, ale te nie są objęte w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="7a6ae-135">W tej przykładowej zabezpieczeń niestandardowych dziedziczy Menedżer tokenów <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy i zastąpień `CreateSecurityTokenProvider` żądanej metody do zwracania niestandardowego dostawcy tokenu SAML podczas przekazany wymagania tokenu wskazują, że tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="7a6ae-136">Jeśli klasa poświadczeń klienta nie (zobacz krok 3) określił potwierdzenia, Menedżer tokenów zabezpieczających tworzy odpowiednie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>  
  
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
  
3.  <span data-ttu-id="7a6ae-137">Wpisz poświadczenia niestandardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-137">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="7a6ae-138">Klasa poświadczeń klienta jest używana do reprezentowania poświadczenia, które są skonfigurowane dla serwera proxy klienta i tworzy Menedżer tokenów, który jest używany do uzyskania wystawcy uwierzytelnienia tokenu, dostawcy tokenów i Serializator tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>  
  
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
  
4.  <span data-ttu-id="7a6ae-139">Skonfigurować klienta do używania poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-139">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="7a6ae-140">Próbka usuwa domyślną klasę poświadczeń klienta i udostępnia nową klasę poświadczeń klienta, klient może używać poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>  
  
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
  
 <span data-ttu-id="7a6ae-141">W usłudze oświadczeń skojarzone z funkcją wywołującą są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="7a6ae-142">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7a6ae-143">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-143">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="7a6ae-144">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="7a6ae-144">Setup Batch File</span></span>  
 <span data-ttu-id="7a6ae-145">Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiedni certyfikat do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="7a6ae-146">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="7a6ae-147">Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="7a6ae-148">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="7a6ae-148">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="7a6ae-149">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="7a6ae-150">`%SERVER_NAME%` Zmiennej określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="7a6ae-151">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="7a6ae-152">Wartość domyślna w tym pliku wsadowego to localhost.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-152">The default value in this batch file is localhost.</span></span>  
  
     <span data-ttu-id="7a6ae-153">Certyfikat jest przechowywany w magazynie LocalMachine lokalizacji w mojej (osobiste).</span><span class="sxs-lookup"><span data-stu-id="7a6ae-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="7a6ae-154">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="7a6ae-154">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="7a6ae-155">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7a6ae-156">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7a6ae-157">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="7a6ae-158">Tworzenie wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-158">Creating the issuer certificate.</span></span>  
  
     <span data-ttu-id="7a6ae-159">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzyć wystawcy certyfikatu do użycia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="7a6ae-160">`%USER_NAME%` Zmiennej Nazwa wystawcy.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="7a6ae-161">Zmień tę wartość, aby określić nazwę wystawcy.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="7a6ae-162">Wartością domyślną w tym pliku wsadowego jest Alicji.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-162">The default value in this batch file is Alice.</span></span>  
  
     <span data-ttu-id="7a6ae-163">Certyfikat jest przechowywany w magazynie, w My znajdujące się w lokalizacji magazynie CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-163">The certificate is stored in My store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="7a6ae-164">Instalowanie wystawcy certyfikatu do magazynu zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="7a6ae-165">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7a6ae-166">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7a6ae-167">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów na serwerze przy użyciu certyfikatu wystawcy nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7a6ae-168">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="7a6ae-168">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="7a6ae-169">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a6ae-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7a6ae-170">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7a6ae-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6ae-171">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7a6ae-172">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="7a6ae-172">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="7a6ae-173">Uruchom z folderu instalacji próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-173">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="7a6ae-174">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-174">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a6ae-175">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-175">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="7a6ae-176">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-176">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="7a6ae-177">Uruchom Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="7a6ae-178">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="7a6ae-179">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="7a6ae-180">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7a6ae-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7a6ae-181">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="7a6ae-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="7a6ae-182">Utwórz katalog na komputerze usługi dla usługi danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="7a6ae-183">Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="7a6ae-184">Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="7a6ae-185">Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="7a6ae-186">Plik Service.exe.config trzeba zaktualizować do uwzględnienia tej nowej nazwy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="7a6ae-187">Można utworzyć certyfikatu serwera, modyfikując plik wsadowy pliku Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="7a6ae-188">Należy pamiętać, że plik pliku setup.bat należy uruchomić w oknie wiersza polecenia programu Visual Studio z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="7a6ae-189">Należy ustawić `%SERVER_NAME%` zmienną do hosta w pełni kwalifikowaną nazwę komputera, na którym jest używany do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="7a6ae-190">Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="7a6ae-191">Ten krok nie jest konieczne, gdy certyfikat serwera jest wystawiony przez klienta zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="7a6ae-192">W pliku Service.exe.config na komputerze usługi Zmień wartość adres podstawowy, aby określić nazwę komputera w pełni kwalifikowaną zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="7a6ae-193">Na komputerze, usługi uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="7a6ae-194">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="7a6ae-195">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="7a6ae-196">Na komputerze klienckim, otwórz `Client.exe` z poziomu okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="7a6ae-197">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7a6ae-197">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7a6ae-198">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="7a6ae-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="7a6ae-199">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6ae-200">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a6ae-200">See Also</span></span>
