---
title: <message> element <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738981"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="e5381-102">\<komunikat > elementu \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e5381-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="e5381-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [\<wsFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e5381-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="e5381-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e5381-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e5381-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e5381-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e5381-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="e5381-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e5381-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WSFederationHttpBinding**](wsfederationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e5381-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e5381-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="e5381-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e5381-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-wsfederationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e5381-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e5381-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<komunikat >**</span><span class="sxs-lookup"><span data-stu-id="e5381-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5381-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5381-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5381-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5381-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e5381-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5381-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5381-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5381-114">Attributes</span></span>  
  
|<span data-ttu-id="e5381-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5381-115">Attribute</span></span>|<span data-ttu-id="e5381-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e5381-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5381-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e5381-117">algorithmSuite</span></span>|<span data-ttu-id="e5381-118">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="e5381-119">Zobacz tabelę "atrybut algorithmSuite", aby uzyskać prawidłowe wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e5381-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="e5381-120">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="e5381-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="e5381-121">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="e5381-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="e5381-122">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="e5381-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="e5381-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="e5381-123">issuedKeyType</span></span>|<span data-ttu-id="e5381-124">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="e5381-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="e5381-125">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e5381-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e5381-126">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="e5381-126">-   SymmetricKey</span></span><br /><span data-ttu-id="e5381-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="e5381-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="e5381-128">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="e5381-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="e5381-129">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="e5381-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="e5381-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="e5381-130">issuedTokenType</span></span>|<span data-ttu-id="e5381-131">Ciąg zawierający identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="e5381-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="e5381-132">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="e5381-132">The default is `null`.</span></span>|  
|<span data-ttu-id="e5381-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="e5381-133">negotiateServiceCredential</span></span>|<span data-ttu-id="e5381-134">Wartość logiczna określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji lub jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="e5381-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="e5381-135">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="e5381-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="e5381-136">algorithmSuite — atrybut</span><span class="sxs-lookup"><span data-stu-id="e5381-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="e5381-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="e5381-137">Value</span></span>|<span data-ttu-id="e5381-138">Opis</span><span class="sxs-lookup"><span data-stu-id="e5381-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e5381-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="e5381-139">Basic128</span></span>|<span data-ttu-id="e5381-140">Użyj szyfrowania Basic128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="e5381-141">Basic192</span></span>|<span data-ttu-id="e5381-142">Użyj szyfrowania Basic192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="e5381-143">Basic256</span></span>|<span data-ttu-id="e5381-144">Użyj szyfrowania Basic256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-145">Basic256Rsa15</span></span>|<span data-ttu-id="e5381-146">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-147">Basic192Rsa15</span></span>|<span data-ttu-id="e5381-148">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="e5381-149">TripleDes</span></span>|<span data-ttu-id="e5381-150">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-151">Basic128Rsa15</span></span>|<span data-ttu-id="e5381-152">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-153">TripleDesRsa15</span></span>|<span data-ttu-id="e5381-154">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="e5381-155">Basic128Sha256</span></span>|<span data-ttu-id="e5381-156">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="e5381-157">Basic192Sha256</span></span>|<span data-ttu-id="e5381-158">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="e5381-159">Basic256Sha256</span></span>|<span data-ttu-id="e5381-160">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="e5381-161">TripleDesSha256</span></span>|<span data-ttu-id="e5381-162">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="e5381-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="e5381-164">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="e5381-166">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="e5381-168">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="e5381-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="e5381-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="e5381-170">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e5381-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5381-171">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5381-171">Child Elements</span></span>  
  
|<span data-ttu-id="e5381-172">Element</span><span class="sxs-lookup"><span data-stu-id="e5381-172">Element</span></span>|<span data-ttu-id="e5381-173">Opis</span><span class="sxs-lookup"><span data-stu-id="e5381-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5381-174">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="e5381-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="e5381-175">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e5381-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="e5381-176">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e5381-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="e5381-177">issuer</span><span class="sxs-lookup"><span data-stu-id="e5381-177">issuer</span></span>|<span data-ttu-id="e5381-178">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="e5381-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="e5381-179">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="e5381-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="e5381-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="e5381-180">issuerMetadata</span></span>|<span data-ttu-id="e5381-181">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="e5381-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="e5381-182">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="e5381-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="e5381-183">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="e5381-183">A collection of token request parameters.</span></span> <span data-ttu-id="e5381-184">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="e5381-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5381-185">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5381-185">Parent Elements</span></span>  
  
|<span data-ttu-id="e5381-186">Element</span><span class="sxs-lookup"><span data-stu-id="e5381-186">Element</span></span>|<span data-ttu-id="e5381-187">Opis</span><span class="sxs-lookup"><span data-stu-id="e5381-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5381-188">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="e5381-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="e5381-189">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="e5381-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5381-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5381-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="e5381-191">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e5381-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e5381-192">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e5381-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e5381-193">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e5381-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e5381-194">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e5381-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e5381-195">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="e5381-195">\<binding></span></span>](bindings.md)
