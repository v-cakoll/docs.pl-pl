---
title: <message>elementu<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 4730d7e573eefdfcd5704621d0a7ccaa15f76d3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931579"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="989f2-102">\<komunikat > elementu \<WSFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="989f2-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="989f2-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<> WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="989f2-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="989f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="989f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="989f2-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="989f2-105">\<bindings></span></span>  
<span data-ttu-id="989f2-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="989f2-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="989f2-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="989f2-107">\<binding></span></span>  
<span data-ttu-id="989f2-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="989f2-108">\<security></span></span>  
<span data-ttu-id="989f2-109">\<message></span><span class="sxs-lookup"><span data-stu-id="989f2-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989f2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="989f2-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="989f2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="989f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="989f2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="989f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="989f2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="989f2-113">Attributes</span></span>  
  
|<span data-ttu-id="989f2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="989f2-114">Attribute</span></span>|<span data-ttu-id="989f2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="989f2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="989f2-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="989f2-116">algorithmSuite</span></span>|<span data-ttu-id="989f2-117">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="989f2-118">Zobacz tabelę "atrybut algorithmSuite", aby uzyskać prawidłowe wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="989f2-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="989f2-119">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="989f2-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="989f2-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="989f2-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="989f2-121">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="989f2-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="989f2-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="989f2-122">issuedKeyType</span></span>|<span data-ttu-id="989f2-123">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="989f2-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="989f2-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="989f2-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="989f2-125">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="989f2-125">-   SymmetricKey</span></span><br /><span data-ttu-id="989f2-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="989f2-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="989f2-127">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="989f2-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="989f2-128">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="989f2-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="989f2-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="989f2-129">issuedTokenType</span></span>|<span data-ttu-id="989f2-130">Ciąg zawierający identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="989f2-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="989f2-131">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="989f2-131">The default is `null`.</span></span>|  
|<span data-ttu-id="989f2-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="989f2-132">negotiateServiceCredential</span></span>|<span data-ttu-id="989f2-133">Wartość logiczna określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji lub jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="989f2-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="989f2-134">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="989f2-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="989f2-135">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="989f2-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="989f2-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="989f2-136">Value</span></span>|<span data-ttu-id="989f2-137">Opis</span><span class="sxs-lookup"><span data-stu-id="989f2-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="989f2-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="989f2-138">Basic128</span></span>|<span data-ttu-id="989f2-139">Użyj szyfrowania Basic128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="989f2-140">Basic192</span></span>|<span data-ttu-id="989f2-141">Użyj szyfrowania Basic192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="989f2-142">Basic256</span></span>|<span data-ttu-id="989f2-143">Użyj szyfrowania Basic256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-144">Basic256Rsa15</span></span>|<span data-ttu-id="989f2-145">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-146">Basic192Rsa15</span></span>|<span data-ttu-id="989f2-147">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="989f2-148">TripleDes</span></span>|<span data-ttu-id="989f2-149">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-150">Basic128Rsa15</span></span>|<span data-ttu-id="989f2-151">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-152">TripleDesRsa15</span></span>|<span data-ttu-id="989f2-153">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="989f2-154">Basic128Sha256</span></span>|<span data-ttu-id="989f2-155">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="989f2-156">Basic192Sha256</span></span>|<span data-ttu-id="989f2-157">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="989f2-158">Basic256Sha256</span></span>|<span data-ttu-id="989f2-159">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="989f2-160">TripleDesSha256</span></span>|<span data-ttu-id="989f2-161">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="989f2-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="989f2-163">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="989f2-165">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="989f2-167">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="989f2-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="989f2-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="989f2-169">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="989f2-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="989f2-170">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="989f2-170">Child Elements</span></span>  
  
|<span data-ttu-id="989f2-171">Element</span><span class="sxs-lookup"><span data-stu-id="989f2-171">Element</span></span>|<span data-ttu-id="989f2-172">Opis</span><span class="sxs-lookup"><span data-stu-id="989f2-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="989f2-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="989f2-173">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="989f2-174">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="989f2-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="989f2-175">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="989f2-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="989f2-176">issuer</span><span class="sxs-lookup"><span data-stu-id="989f2-176">issuer</span></span>|<span data-ttu-id="989f2-177">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="989f2-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="989f2-178">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="989f2-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="989f2-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="989f2-179">issuerMetadata</span></span>|<span data-ttu-id="989f2-180">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="989f2-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="989f2-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="989f2-181">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="989f2-182">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="989f2-182">A collection of token request parameters.</span></span> <span data-ttu-id="989f2-183">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="989f2-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="989f2-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="989f2-184">Parent Elements</span></span>  
  
|<span data-ttu-id="989f2-185">Element</span><span class="sxs-lookup"><span data-stu-id="989f2-185">Element</span></span>|<span data-ttu-id="989f2-186">Opis</span><span class="sxs-lookup"><span data-stu-id="989f2-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="989f2-187">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="989f2-187">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="989f2-188">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="989f2-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="989f2-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="989f2-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="989f2-190">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="989f2-190">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="989f2-191">Powiązania</span><span class="sxs-lookup"><span data-stu-id="989f2-191">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="989f2-192">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="989f2-192">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="989f2-193">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="989f2-193">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="989f2-194">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="989f2-194">\<binding></span></span>](../../../misc/binding.md)
