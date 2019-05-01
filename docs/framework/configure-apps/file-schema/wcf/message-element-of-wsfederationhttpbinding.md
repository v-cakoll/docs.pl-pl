---
title: <message> element <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 79739dd715d7982555e5577c921cb65156af5923
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769879"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="84d82-102">\<komunikat > element \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="84d82-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="84d82-103">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="84d82-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="84d82-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84d82-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="84d82-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="84d82-105">\<bindings></span></span>  
<span data-ttu-id="84d82-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="84d82-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="84d82-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="84d82-107">\<binding></span></span>  
<span data-ttu-id="84d82-108">\<security></span><span class="sxs-lookup"><span data-stu-id="84d82-108">\<security></span></span>  
<span data-ttu-id="84d82-109">\<message></span><span class="sxs-lookup"><span data-stu-id="84d82-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84d82-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="84d82-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84d82-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="84d82-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84d82-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="84d82-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84d82-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="84d82-113">Attributes</span></span>  
  
|<span data-ttu-id="84d82-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="84d82-114">Attribute</span></span>|<span data-ttu-id="84d82-115">Opis</span><span class="sxs-lookup"><span data-stu-id="84d82-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84d82-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="84d82-116">algorithmSuite</span></span>|<span data-ttu-id="84d82-117">Ustawia komunikat algorytmów szyfrowania i zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="84d82-118">Zobacz tabelę "algorithmSuite atrybutu" prawidłowych wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="84d82-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="84d82-119">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="84d82-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="84d82-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="84d82-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="84d82-121">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="84d82-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="84d82-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="84d82-122">issuedKeyType</span></span>|<span data-ttu-id="84d82-123">Określa typ klucza zostanie wysłane.</span><span class="sxs-lookup"><span data-stu-id="84d82-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="84d82-124">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="84d82-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="84d82-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="84d82-125">-   SymmetricKey</span></span><br /><span data-ttu-id="84d82-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="84d82-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="84d82-127">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="84d82-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="84d82-128">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="84d82-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="84d82-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="84d82-129">issuedTokenType</span></span>|<span data-ttu-id="84d82-130">Ciąg, który zawiera identyfikator URI, który określa typ token został wystawiony.</span><span class="sxs-lookup"><span data-stu-id="84d82-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="84d82-131">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="84d82-131">The default is `null`.</span></span>|  
|<span data-ttu-id="84d82-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="84d82-132">negotiateServiceCredential</span></span>|<span data-ttu-id="84d82-133">Wartość logiczna, która określa, czy poświadczenia usługi powinny być wymieniane w ramach negocjacji znajduje się poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="84d82-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="84d82-134">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="84d82-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="84d82-135">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="84d82-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="84d82-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="84d82-136">Value</span></span>|<span data-ttu-id="84d82-137">Opis</span><span class="sxs-lookup"><span data-stu-id="84d82-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84d82-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="84d82-138">Basic128</span></span>|<span data-ttu-id="84d82-139">Użyj szyfrowania Basic128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="84d82-140">Basic192</span></span>|<span data-ttu-id="84d82-141">Należy używać szyfrowania Basic192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="84d82-142">Basic256</span></span>|<span data-ttu-id="84d82-143">Należy używać szyfrowania Basic256, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-144">Basic256Rsa15</span></span>|<span data-ttu-id="84d82-145">Użyj Basic256 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-146">Basic192Rsa15</span></span>|<span data-ttu-id="84d82-147">Użyj Basic192 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="84d82-148">TripleDes</span></span>|<span data-ttu-id="84d82-149">Należy używać szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-150">Basic128Rsa15</span></span>|<span data-ttu-id="84d82-151">Użyj Basic128 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-152">TripleDesRsa15</span></span>|<span data-ttu-id="84d82-153">Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="84d82-154">Basic128Sha256</span></span>|<span data-ttu-id="84d82-155">Użyj Basic128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="84d82-156">Basic192Sha256</span></span>|<span data-ttu-id="84d82-157">Użyj Basic192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="84d82-158">Basic256Sha256</span></span>|<span data-ttu-id="84d82-159">Użyj Basic256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="84d82-160">TripleDesSha256</span></span>|<span data-ttu-id="84d82-161">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="84d82-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="84d82-163">Użyj Basic128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="84d82-165">Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="84d82-167">Użyj Basic256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="84d82-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="84d82-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="84d82-169">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="84d82-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84d82-170">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="84d82-170">Child Elements</span></span>  
  
|<span data-ttu-id="84d82-171">Element</span><span class="sxs-lookup"><span data-stu-id="84d82-171">Element</span></span>|<span data-ttu-id="84d82-172">Opis</span><span class="sxs-lookup"><span data-stu-id="84d82-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84d82-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="84d82-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="84d82-174">Określa kolekcję typów oświadczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="84d82-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="84d82-175">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="84d82-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="84d82-176">issuer</span><span class="sxs-lookup"><span data-stu-id="84d82-176">issuer</span></span>|<span data-ttu-id="84d82-177">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="84d82-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="84d82-178">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="84d82-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="84d82-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="84d82-179">issuerMetadata</span></span>|<span data-ttu-id="84d82-180">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="84d82-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="84d82-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="84d82-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="84d82-182">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="84d82-182">A collection of token request parameters.</span></span> <span data-ttu-id="84d82-183">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="84d82-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84d82-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="84d82-184">Parent Elements</span></span>  
  
|<span data-ttu-id="84d82-185">Element</span><span class="sxs-lookup"><span data-stu-id="84d82-185">Element</span></span>|<span data-ttu-id="84d82-186">Opis</span><span class="sxs-lookup"><span data-stu-id="84d82-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84d82-187">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="84d82-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="84d82-188">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="84d82-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84d82-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84d82-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="84d82-190">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="84d82-190">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="84d82-191">Powiązania</span><span class="sxs-lookup"><span data-stu-id="84d82-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="84d82-192">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="84d82-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="84d82-193">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="84d82-193">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="84d82-194">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="84d82-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
