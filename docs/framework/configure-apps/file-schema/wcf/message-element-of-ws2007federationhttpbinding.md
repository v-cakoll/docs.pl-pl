---
title: '&lt;message&gt; w &lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 6954a7b9646b35ee03aab311deae026a711be9cd
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847558"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="d684f-102">&lt;message&gt; w &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d684f-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="d684f-103">Definiuje ustawienia zabezpieczeń na poziomie komunikatu dla [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d684f-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="d684f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d684f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d684f-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d684f-105">\<bindings></span></span>  
<span data-ttu-id="d684f-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d684f-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="d684f-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d684f-107">\<binding></span></span>  
<span data-ttu-id="d684f-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d684f-108">\<security></span></span>  
<span data-ttu-id="d684f-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d684f-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d684f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d684f-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
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
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d684f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d684f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d684f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d684f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d684f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d684f-113">Attributes</span></span>  
  
|<span data-ttu-id="d684f-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d684f-114">Attribute</span></span>|<span data-ttu-id="d684f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d684f-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="d684f-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d684f-116">Optional.</span></span> <span data-ttu-id="d684f-117">Ustawia szyfrowania wiadomości, podpis i algorytmów klucza zawijania.</span><span class="sxs-lookup"><span data-stu-id="d684f-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="d684f-118">Te algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasy.</span><span class="sxs-lookup"><span data-stu-id="d684f-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="d684f-119">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="d684f-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="d684f-120">Zobacz poniższą tabelę prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="d684f-120">See the following table for possible values.</span></span> <span data-ttu-id="d684f-121">Wartość domyślna to Basic256.</span><span class="sxs-lookup"><span data-stu-id="d684f-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="d684f-122">Określa typ klucza zostanie wysłane.</span><span class="sxs-lookup"><span data-stu-id="d684f-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="d684f-123">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d684f-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d684f-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="d684f-124">-   SymmetricKey</span></span><br /><span data-ttu-id="d684f-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="d684f-125">-   PublicKey</span></span><br /><span data-ttu-id="d684f-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="d684f-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="d684f-127">Wartość domyślna to SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="d684f-127">The default is SymmetricKey.</span></span> <span data-ttu-id="d684f-128">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="d684f-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="d684f-129">Identyfikator URI, który określa typ token został wystawiony.</span><span class="sxs-lookup"><span data-stu-id="d684f-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="d684f-130">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="d684f-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="d684f-131">Wartość, która określa, czy poświadczenia usługi powinny być wymieniane w ramach negocjacji znajduje się poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="d684f-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="d684f-132">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="d684f-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="d684f-133">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="d684f-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="d684f-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="d684f-134">Value</span></span>|<span data-ttu-id="d684f-135">Opis</span><span class="sxs-lookup"><span data-stu-id="d684f-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d684f-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="d684f-136">Basic128</span></span>|<span data-ttu-id="d684f-137">Użyj szyfrowania Aes128, Sha1 dla skrót wiadomości i Rsa-oaep-mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="d684f-138">Basic192</span></span>|<span data-ttu-id="d684f-139">Należy używać szyfrowania Aes192, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="d684f-140">Basic256</span></span>|<span data-ttu-id="d684f-141">Użyj szyfrowania Aes256 Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-142">Basic256Rsa15</span></span>|<span data-ttu-id="d684f-143">Użyj Aes256 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-144">Basic192Rsa15</span></span>|<span data-ttu-id="d684f-145">Użyj Aes192 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="d684f-146">TripleDes</span></span>|<span data-ttu-id="d684f-147">Należy używać szyfrowania TripleDes, Sha1 dla skrót wiadomości, Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-148">Basic128Rsa15</span></span>|<span data-ttu-id="d684f-149">Użyj Aes128 do szyfrowania wiadomości, algorytm Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-150">TripleDesRsa15</span></span>|<span data-ttu-id="d684f-151">Użyj szyfrowania TripleDes, Sha1 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="d684f-152">Basic128Sha256</span></span>|<span data-ttu-id="d684f-153">Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="d684f-154">Basic192Sha256</span></span>|<span data-ttu-id="d684f-155">Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="d684f-156">Basic256Sha256</span></span>|<span data-ttu-id="d684f-157">Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="d684f-158">TripleDesSha256</span></span>|<span data-ttu-id="d684f-159">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa oaep mgf1p dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d684f-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="d684f-161">Użyj Aes128 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="d684f-163">Użyj Aes192 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="d684f-165">Użyj Aes256 do szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d684f-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d684f-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="d684f-167">TripleDes na użytek szyfrowania wiadomości, Sha256 dla skrót wiadomości i Rsa15 dla zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="d684f-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d684f-168">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d684f-168">Child Elements</span></span>  
  
|<span data-ttu-id="d684f-169">Element</span><span class="sxs-lookup"><span data-stu-id="d684f-169">Element</span></span>|<span data-ttu-id="d684f-170">Opis</span><span class="sxs-lookup"><span data-stu-id="d684f-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d684f-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d684f-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="d684f-172">Określa kolekcję typów oświadczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d684f-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="d684f-173">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d684f-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="d684f-174">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="d684f-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="d684f-175">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="d684f-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="d684f-176">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="d684f-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="d684f-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="d684f-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="d684f-178">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="d684f-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="d684f-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="d684f-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="d684f-180">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="d684f-180">A collection of token request parameters.</span></span> <span data-ttu-id="d684f-181">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="d684f-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d684f-182">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d684f-182">Parent Elements</span></span>  
  
|<span data-ttu-id="d684f-183">Element</span><span class="sxs-lookup"><span data-stu-id="d684f-183">Element</span></span>|<span data-ttu-id="d684f-184">Opis</span><span class="sxs-lookup"><span data-stu-id="d684f-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d684f-185">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d684f-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="d684f-186">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d684f-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d684f-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d684f-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="d684f-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="d684f-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="d684f-189">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d684f-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d684f-190">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="d684f-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d684f-191">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d684f-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="d684f-192">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d684f-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
