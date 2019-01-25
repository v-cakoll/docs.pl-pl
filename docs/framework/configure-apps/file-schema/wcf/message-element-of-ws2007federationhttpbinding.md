---
title: '&lt;message&gt; w &lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 280d92978dba44d3347699959fb2cab3b98faca1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493810"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="63ea0-102">&lt;message&gt; w &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="63ea0-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="63ea0-103">Definiuje ustawienia zabezpieczeń na poziomie komunikatu dla [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="63ea0-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="63ea0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63ea0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63ea0-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="63ea0-105">\<bindings></span></span>  
<span data-ttu-id="63ea0-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="63ea0-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="63ea0-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="63ea0-107">\<binding></span></span>  
<span data-ttu-id="63ea0-108">\<security></span><span class="sxs-lookup"><span data-stu-id="63ea0-108">\<security></span></span>  
<span data-ttu-id="63ea0-109">\<message></span><span class="sxs-lookup"><span data-stu-id="63ea0-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63ea0-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="63ea0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63ea0-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63ea0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63ea0-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="63ea0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63ea0-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63ea0-113">Attributes</span></span>  
  
|<span data-ttu-id="63ea0-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="63ea0-114">Attribute</span></span>|<span data-ttu-id="63ea0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="63ea0-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="63ea0-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="63ea0-116">Optional.</span></span> <span data-ttu-id="63ea0-117">Ustawia szyfrowania wiadomości, podpis i algorytmów klucza zawijania.</span><span class="sxs-lookup"><span data-stu-id="63ea0-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="63ea0-118">Te algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy.</span><span class="sxs-lookup"><span data-stu-id="63ea0-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="63ea0-119">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="63ea0-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="63ea0-120">Zobacz poniższą tabelę prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="63ea0-120">See the following table for possible values.</span></span> <span data-ttu-id="63ea0-121">Wartość domyślna to Basic256.</span><span class="sxs-lookup"><span data-stu-id="63ea0-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="63ea0-122">Określa typ klucza zostanie wysłane.</span><span class="sxs-lookup"><span data-stu-id="63ea0-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="63ea0-123">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="63ea0-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="63ea0-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="63ea0-124">-   SymmetricKey</span></span><br /><span data-ttu-id="63ea0-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="63ea0-125">-   PublicKey</span></span><br /><span data-ttu-id="63ea0-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="63ea0-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="63ea0-127">Wartość domyślna to SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="63ea0-127">The default is SymmetricKey.</span></span> <span data-ttu-id="63ea0-128">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="63ea0-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="63ea0-129">Identyfikator URI, który określa typ token został wystawiony.</span><span class="sxs-lookup"><span data-stu-id="63ea0-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="63ea0-130">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="63ea0-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="63ea0-131">Wartość, która określa, czy poświadczenia usługi powinny być wymieniane w ramach negocjacji znajduje się poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="63ea0-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="63ea0-132">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="63ea0-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="63ea0-133">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="63ea0-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="63ea0-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="63ea0-134">Value</span></span>|<span data-ttu-id="63ea0-135">Opis</span><span class="sxs-lookup"><span data-stu-id="63ea0-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63ea0-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="63ea0-136">Basic128</span></span>|<span data-ttu-id="63ea0-137">Użyj szyfrowania Aes128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="63ea0-138">Basic192</span></span>|<span data-ttu-id="63ea0-139">Należy używać szyfrowania Aes192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="63ea0-140">Basic256</span></span>|<span data-ttu-id="63ea0-141">Użyj szyfrowania Aes256 Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-142">Basic256Rsa15</span></span>|<span data-ttu-id="63ea0-143">Użyj Aes256 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-144">Basic192Rsa15</span></span>|<span data-ttu-id="63ea0-145">Użyj Aes192 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="63ea0-146">TripleDes</span></span>|<span data-ttu-id="63ea0-147">Należy używać szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-148">Basic128Rsa15</span></span>|<span data-ttu-id="63ea0-149">Użyj Aes128 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-150">TripleDesRsa15</span></span>|<span data-ttu-id="63ea0-151">Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="63ea0-152">Basic128Sha256</span></span>|<span data-ttu-id="63ea0-153">Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="63ea0-154">Basic192Sha256</span></span>|<span data-ttu-id="63ea0-155">Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="63ea0-156">Basic256Sha256</span></span>|<span data-ttu-id="63ea0-157">Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="63ea0-158">TripleDesSha256</span></span>|<span data-ttu-id="63ea0-159">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="63ea0-161">Użyj Aes128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="63ea0-163">Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="63ea0-165">Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63ea0-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63ea0-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="63ea0-167">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="63ea0-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63ea0-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63ea0-168">Child Elements</span></span>  
  
|<span data-ttu-id="63ea0-169">Element</span><span class="sxs-lookup"><span data-stu-id="63ea0-169">Element</span></span>|<span data-ttu-id="63ea0-170">Opis</span><span class="sxs-lookup"><span data-stu-id="63ea0-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63ea0-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="63ea0-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="63ea0-172">Określa kolekcję typów oświadczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="63ea0-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="63ea0-173">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="63ea0-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="63ea0-174">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="63ea0-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="63ea0-175">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="63ea0-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="63ea0-176">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="63ea0-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="63ea0-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="63ea0-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="63ea0-178">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="63ea0-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="63ea0-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="63ea0-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="63ea0-180">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="63ea0-180">A collection of token request parameters.</span></span> <span data-ttu-id="63ea0-181">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="63ea0-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63ea0-182">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63ea0-182">Parent Elements</span></span>  
  
|<span data-ttu-id="63ea0-183">Element</span><span class="sxs-lookup"><span data-stu-id="63ea0-183">Element</span></span>|<span data-ttu-id="63ea0-184">Opis</span><span class="sxs-lookup"><span data-stu-id="63ea0-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63ea0-185">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="63ea0-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="63ea0-186">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="63ea0-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63ea0-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63ea0-187">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement` 
- [<span data-ttu-id="63ea0-188">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="63ea0-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="63ea0-189">Powiązania</span><span class="sxs-lookup"><span data-stu-id="63ea0-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="63ea0-190">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="63ea0-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="63ea0-191">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="63ea0-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="63ea0-192">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="63ea0-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
