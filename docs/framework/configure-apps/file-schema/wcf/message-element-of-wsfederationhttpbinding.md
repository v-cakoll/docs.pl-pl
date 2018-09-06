---
title: '&lt;message&gt; w &lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 820ee7015a51ecc5510889516faef20292cfbc07
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871267"
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="24116-102">&lt;message&gt; w &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="24116-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="24116-103">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="24116-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="24116-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24116-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="24116-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="24116-105">\<bindings></span></span>  
<span data-ttu-id="24116-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="24116-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="24116-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="24116-107">\<binding></span></span>  
<span data-ttu-id="24116-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="24116-108">\<security></span></span>  
<span data-ttu-id="24116-109">\<message></span><span class="sxs-lookup"><span data-stu-id="24116-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24116-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="24116-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
     <binding >  
         <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                              <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24116-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24116-111">Attributes and Elements</span></span>  
 <span data-ttu-id="24116-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24116-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24116-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24116-113">Attributes</span></span>  
  
|<span data-ttu-id="24116-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24116-114">Attribute</span></span>|<span data-ttu-id="24116-115">Opis</span><span class="sxs-lookup"><span data-stu-id="24116-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24116-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="24116-116">algorithmSuite</span></span>|<span data-ttu-id="24116-117">Ustawia komunikat algorytmów szyfrowania i zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="24116-118">Zobacz tabelę "algorithmSuite atrybutu" prawidłowych wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="24116-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="24116-119">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="24116-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="24116-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="24116-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="24116-121">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="24116-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="24116-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="24116-122">issuedKeyType</span></span>|<span data-ttu-id="24116-123">Określa typ klucza zostanie wysłane.</span><span class="sxs-lookup"><span data-stu-id="24116-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="24116-124">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="24116-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="24116-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="24116-125">-   SymmetricKey</span></span><br /><span data-ttu-id="24116-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="24116-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="24116-127">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="24116-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="24116-128">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="24116-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="24116-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="24116-129">issuedTokenType</span></span>|<span data-ttu-id="24116-130">Ciąg, który zawiera identyfikator URI, który określa typ token został wystawiony.</span><span class="sxs-lookup"><span data-stu-id="24116-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="24116-131">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="24116-131">The default is `null`.</span></span>|  
|<span data-ttu-id="24116-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="24116-132">negotiateServiceCredential</span></span>|<span data-ttu-id="24116-133">Wartość logiczna, która określa, czy poświadczenia usługi powinny być wymieniane w ramach negocjacji znajduje się poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="24116-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="24116-134">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="24116-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="24116-135">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="24116-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="24116-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="24116-136">Value</span></span>|<span data-ttu-id="24116-137">Opis</span><span class="sxs-lookup"><span data-stu-id="24116-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24116-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="24116-138">Basic128</span></span>|<span data-ttu-id="24116-139">Użyj szyfrowania Basic128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="24116-140">Basic192</span></span>|<span data-ttu-id="24116-141">Należy używać szyfrowania Basic192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="24116-142">Basic256</span></span>|<span data-ttu-id="24116-143">Należy używać szyfrowania Basic256, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-144">Basic256Rsa15</span></span>|<span data-ttu-id="24116-145">Użyj Basic256 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-146">Basic192Rsa15</span></span>|<span data-ttu-id="24116-147">Użyj Basic192 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="24116-148">TripleDes</span></span>|<span data-ttu-id="24116-149">Należy używać szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-150">Basic128Rsa15</span></span>|<span data-ttu-id="24116-151">Użyj Basic128 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="24116-152">TripleDesRsa15</span></span>|<span data-ttu-id="24116-153">Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="24116-154">Basic128Sha256</span></span>|<span data-ttu-id="24116-155">Użyj Basic128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="24116-156">Basic192Sha256</span></span>|<span data-ttu-id="24116-157">Użyj Basic192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="24116-158">Basic256Sha256</span></span>|<span data-ttu-id="24116-159">Użyj Basic256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="24116-160">TripleDesSha256</span></span>|<span data-ttu-id="24116-161">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="24116-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="24116-163">Użyj Basic128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="24116-165">Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="24116-167">Użyj Basic256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="24116-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="24116-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="24116-169">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="24116-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24116-170">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24116-170">Child Elements</span></span>  
  
|<span data-ttu-id="24116-171">Element</span><span class="sxs-lookup"><span data-stu-id="24116-171">Element</span></span>|<span data-ttu-id="24116-172">Opis</span><span class="sxs-lookup"><span data-stu-id="24116-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24116-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="24116-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="24116-174">Określa kolekcję typów oświadczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="24116-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="24116-175">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="24116-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="24116-176">issuer</span><span class="sxs-lookup"><span data-stu-id="24116-176">issuer</span></span>|<span data-ttu-id="24116-177">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="24116-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="24116-178">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="24116-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="24116-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="24116-179">issuerMetadata</span></span>|<span data-ttu-id="24116-180">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="24116-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="24116-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="24116-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="24116-182">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="24116-182">A collection of token request parameters.</span></span> <span data-ttu-id="24116-183">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="24116-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24116-184">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24116-184">Parent Elements</span></span>  
  
|<span data-ttu-id="24116-185">Element</span><span class="sxs-lookup"><span data-stu-id="24116-185">Element</span></span>|<span data-ttu-id="24116-186">Opis</span><span class="sxs-lookup"><span data-stu-id="24116-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24116-187">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="24116-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="24116-188">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="24116-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24116-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24116-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="24116-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="24116-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="24116-191">Powiązania</span><span class="sxs-lookup"><span data-stu-id="24116-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="24116-192">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="24116-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="24116-193">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="24116-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="24116-194">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="24116-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
