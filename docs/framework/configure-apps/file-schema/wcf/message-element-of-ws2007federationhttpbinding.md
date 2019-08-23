---
title: <message>elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 4340727026cb151f2efe813dfa005c1c5a1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931623"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="9f529-102">\<komunikat > elementu \<WS2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9f529-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="9f529-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<elementu ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9f529-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="9f529-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f529-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f529-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="9f529-105">\<bindings></span></span>  
<span data-ttu-id="9f529-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9f529-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="9f529-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9f529-107">\<binding></span></span>  
<span data-ttu-id="9f529-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9f529-108">\<security></span></span>  
<span data-ttu-id="9f529-109">\<message></span><span class="sxs-lookup"><span data-stu-id="9f529-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f529-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f529-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
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
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f529-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9f529-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f529-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9f529-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f529-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f529-113">Attributes</span></span>  
  
|<span data-ttu-id="9f529-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9f529-114">Attribute</span></span>|<span data-ttu-id="9f529-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9f529-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="9f529-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9f529-116">Optional.</span></span> <span data-ttu-id="9f529-117">Ustawia szyfrowanie wiadomości, sygnaturę i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="9f529-118">Algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasę.</span><span class="sxs-lookup"><span data-stu-id="9f529-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="9f529-119">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="9f529-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="9f529-120">Zapoznaj się z poniższą tabelą, aby poznać możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="9f529-120">See the following table for possible values.</span></span> <span data-ttu-id="9f529-121">Wartość domyślna to Basic256.</span><span class="sxs-lookup"><span data-stu-id="9f529-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="9f529-122">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="9f529-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="9f529-123">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9f529-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9f529-124">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="9f529-124">-   SymmetricKey</span></span><br /><span data-ttu-id="9f529-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="9f529-125">-   PublicKey</span></span><br /><span data-ttu-id="9f529-126">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="9f529-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="9f529-127">Wartość domyślna to SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="9f529-127">The default is SymmetricKey.</span></span> <span data-ttu-id="9f529-128">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="9f529-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="9f529-129">Identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="9f529-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="9f529-130">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="9f529-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="9f529-131">Wartość określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji, czy też jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="9f529-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="9f529-132">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="9f529-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="9f529-133">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="9f529-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="9f529-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="9f529-134">Value</span></span>|<span data-ttu-id="9f529-135">Opis</span><span class="sxs-lookup"><span data-stu-id="9f529-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f529-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="9f529-136">Basic128</span></span>|<span data-ttu-id="9f529-137">Użyj szyfrowania Aes128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="9f529-138">Basic192</span></span>|<span data-ttu-id="9f529-139">Użyj szyfrowania Aes192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="9f529-140">Basic256</span></span>|<span data-ttu-id="9f529-141">Użyj szyfrowania AES256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-142">Basic256Rsa15</span></span>|<span data-ttu-id="9f529-143">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-144">Basic192Rsa15</span></span>|<span data-ttu-id="9f529-145">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="9f529-146">TripleDes</span></span>|<span data-ttu-id="9f529-147">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-148">Basic128Rsa15</span></span>|<span data-ttu-id="9f529-149">Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-150">TripleDesRsa15</span></span>|<span data-ttu-id="9f529-151">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="9f529-152">Basic128Sha256</span></span>|<span data-ttu-id="9f529-153">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="9f529-154">Basic192Sha256</span></span>|<span data-ttu-id="9f529-155">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="9f529-156">Basic256Sha256</span></span>|<span data-ttu-id="9f529-157">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="9f529-158">TripleDesSha256</span></span>|<span data-ttu-id="9f529-159">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9f529-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="9f529-161">Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="9f529-163">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="9f529-165">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9f529-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9f529-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="9f529-167">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f529-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f529-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f529-168">Child Elements</span></span>  
  
|<span data-ttu-id="9f529-169">Element</span><span class="sxs-lookup"><span data-stu-id="9f529-169">Element</span></span>|<span data-ttu-id="9f529-170">Opis</span><span class="sxs-lookup"><span data-stu-id="9f529-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f529-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="9f529-171">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="9f529-172">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9f529-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="9f529-173">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="9f529-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="9f529-174">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="9f529-174">\<issuer></span></span>](issuer.md)|<span data-ttu-id="9f529-175">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="9f529-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="9f529-176">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="9f529-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="9f529-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="9f529-177">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="9f529-178">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="9f529-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="9f529-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="9f529-179">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="9f529-180">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="9f529-180">A collection of token request parameters.</span></span> <span data-ttu-id="9f529-181">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="9f529-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f529-182">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9f529-182">Parent Elements</span></span>  
  
|<span data-ttu-id="9f529-183">Element</span><span class="sxs-lookup"><span data-stu-id="9f529-183">Element</span></span>|<span data-ttu-id="9f529-184">Opis</span><span class="sxs-lookup"><span data-stu-id="9f529-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f529-185">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9f529-185">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="9f529-186">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="9f529-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f529-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f529-187">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="9f529-188">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9f529-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9f529-189">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9f529-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f529-190">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="9f529-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9f529-191">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="9f529-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9f529-192">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="9f529-192">\<binding></span></span>](../../../misc/binding.md)
