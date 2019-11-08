---
title: <message> element <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738997"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="c609f-102">\<komunikat > elementu \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c609f-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="c609f-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla elementu [\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c609f-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="c609f-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c609f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c609f-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c609f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c609f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="c609f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c609f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WS2007FederationHttpBinding**](ws2007federationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="c609f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="c609f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="c609f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c609f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-element-of-ws2007federationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="c609f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="c609f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<komunikat >**</span><span class="sxs-lookup"><span data-stu-id="c609f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c609f-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="c609f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c609f-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c609f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c609f-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c609f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c609f-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c609f-114">Attributes</span></span>  
  
|<span data-ttu-id="c609f-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c609f-115">Attribute</span></span>|<span data-ttu-id="c609f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c609f-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="c609f-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c609f-117">Optional.</span></span> <span data-ttu-id="c609f-118">Ustawia szyfrowanie wiadomości, sygnaturę i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="c609f-119">Algorytmy i rozmiary kluczy są określane przez klasę <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="c609f-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="c609f-120">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="c609f-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="c609f-121">Zapoznaj się z poniższą tabelą, aby poznać możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="c609f-121">See the following table for possible values.</span></span> <span data-ttu-id="c609f-122">Wartość domyślna to Basic256.</span><span class="sxs-lookup"><span data-stu-id="c609f-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="c609f-123">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="c609f-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="c609f-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="c609f-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c609f-125">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="c609f-125">-   SymmetricKey</span></span><br /><span data-ttu-id="c609f-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="c609f-126">-   PublicKey</span></span><br /><span data-ttu-id="c609f-127">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="c609f-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="c609f-128">Wartość domyślna to SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="c609f-128">The default is SymmetricKey.</span></span> <span data-ttu-id="c609f-129">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="c609f-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="c609f-130">Identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="c609f-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="c609f-131">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="c609f-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="c609f-132">Wartość określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji, czy też jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="c609f-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="c609f-133">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="c609f-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="c609f-134">algorithmSuite — atrybut</span><span class="sxs-lookup"><span data-stu-id="c609f-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="c609f-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="c609f-135">Value</span></span>|<span data-ttu-id="c609f-136">Opis</span><span class="sxs-lookup"><span data-stu-id="c609f-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c609f-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="c609f-137">Basic128</span></span>|<span data-ttu-id="c609f-138">Użyj szyfrowania Aes128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="c609f-139">Basic192</span></span>|<span data-ttu-id="c609f-140">Użyj szyfrowania Aes192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="c609f-141">Basic256</span></span>|<span data-ttu-id="c609f-142">Użyj szyfrowania AES256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-143">Basic256Rsa15</span></span>|<span data-ttu-id="c609f-144">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-145">Basic192Rsa15</span></span>|<span data-ttu-id="c609f-146">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="c609f-147">TripleDes</span></span>|<span data-ttu-id="c609f-148">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-149">Basic128Rsa15</span></span>|<span data-ttu-id="c609f-150">Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-151">TripleDesRsa15</span></span>|<span data-ttu-id="c609f-152">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="c609f-153">Basic128Sha256</span></span>|<span data-ttu-id="c609f-154">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="c609f-155">Basic192Sha256</span></span>|<span data-ttu-id="c609f-156">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="c609f-157">Basic256Sha256</span></span>|<span data-ttu-id="c609f-158">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="c609f-159">TripleDesSha256</span></span>|<span data-ttu-id="c609f-160">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c609f-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="c609f-162">Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="c609f-164">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="c609f-166">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c609f-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c609f-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="c609f-168">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="c609f-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c609f-169">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c609f-169">Child Elements</span></span>  
  
|<span data-ttu-id="c609f-170">Element</span><span class="sxs-lookup"><span data-stu-id="c609f-170">Element</span></span>|<span data-ttu-id="c609f-171">Opis</span><span class="sxs-lookup"><span data-stu-id="c609f-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c609f-172">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="c609f-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="c609f-173">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c609f-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="c609f-174">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="c609f-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="c609f-175">\<wystawcy ></span><span class="sxs-lookup"><span data-stu-id="c609f-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="c609f-176">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="c609f-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="c609f-177">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="c609f-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="c609f-178">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="c609f-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="c609f-179">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="c609f-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="c609f-180">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="c609f-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="c609f-181">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="c609f-181">A collection of token request parameters.</span></span> <span data-ttu-id="c609f-182">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="c609f-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c609f-183">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c609f-183">Parent Elements</span></span>  
  
|<span data-ttu-id="c609f-184">Element</span><span class="sxs-lookup"><span data-stu-id="c609f-184">Element</span></span>|<span data-ttu-id="c609f-185">Opis</span><span class="sxs-lookup"><span data-stu-id="c609f-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c609f-186">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="c609f-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="c609f-187">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="c609f-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c609f-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c609f-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="c609f-189">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c609f-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c609f-190">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c609f-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c609f-191">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c609f-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c609f-192">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c609f-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c609f-193">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="c609f-193">\<binding></span></span>](bindings.md)
