---
title: <message>elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: b1128bda6068a1fe3d8f5bb5ac29cc349f023b5b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397852"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="dea8c-102">\<komunikat > elementu \<WS2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dea8c-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="dea8c-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<elementu ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dea8c-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="dea8c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dea8c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dea8c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dea8c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dea8c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="dea8c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dea8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dea8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="dea8c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="dea8c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="dea8c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dea8c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="dea8c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> komunikatu**</span><span class="sxs-lookup"><span data-stu-id="dea8c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea8c-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="dea8c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dea8c-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dea8c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dea8c-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dea8c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dea8c-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dea8c-114">Attributes</span></span>  
  
|<span data-ttu-id="dea8c-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dea8c-115">Attribute</span></span>|<span data-ttu-id="dea8c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="dea8c-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="dea8c-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="dea8c-117">Optional.</span></span> <span data-ttu-id="dea8c-118">Ustawia szyfrowanie wiadomości, sygnaturę i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="dea8c-119">Algorytmy i rozmiary kluczy są określane przez <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> klasę.</span><span class="sxs-lookup"><span data-stu-id="dea8c-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="dea8c-120">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="dea8c-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="dea8c-121">Zapoznaj się z poniższą tabelą, aby poznać możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="dea8c-121">See the following table for possible values.</span></span> <span data-ttu-id="dea8c-122">Wartość domyślna to Basic256.</span><span class="sxs-lookup"><span data-stu-id="dea8c-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="dea8c-123">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="dea8c-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="dea8c-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dea8c-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dea8c-125">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="dea8c-125">-   SymmetricKey</span></span><br /><span data-ttu-id="dea8c-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="dea8c-126">-   PublicKey</span></span><br /><span data-ttu-id="dea8c-127">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="dea8c-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="dea8c-128">Wartość domyślna to SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="dea8c-128">The default is SymmetricKey.</span></span> <span data-ttu-id="dea8c-129">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="dea8c-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="dea8c-130">Identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="dea8c-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="dea8c-131">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="dea8c-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="dea8c-132">Wartość określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji, czy też jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="dea8c-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="dea8c-133">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="dea8c-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="dea8c-134">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="dea8c-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="dea8c-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="dea8c-135">Value</span></span>|<span data-ttu-id="dea8c-136">Opis</span><span class="sxs-lookup"><span data-stu-id="dea8c-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dea8c-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="dea8c-137">Basic128</span></span>|<span data-ttu-id="dea8c-138">Użyj szyfrowania Aes128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="dea8c-139">Basic192</span></span>|<span data-ttu-id="dea8c-140">Użyj szyfrowania Aes192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="dea8c-141">Basic256</span></span>|<span data-ttu-id="dea8c-142">Użyj szyfrowania AES256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-143">Basic256Rsa15</span></span>|<span data-ttu-id="dea8c-144">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-145">Basic192Rsa15</span></span>|<span data-ttu-id="dea8c-146">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="dea8c-147">TripleDes</span></span>|<span data-ttu-id="dea8c-148">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-149">Basic128Rsa15</span></span>|<span data-ttu-id="dea8c-150">Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-151">TripleDesRsa15</span></span>|<span data-ttu-id="dea8c-152">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="dea8c-153">Basic128Sha256</span></span>|<span data-ttu-id="dea8c-154">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="dea8c-155">Basic192Sha256</span></span>|<span data-ttu-id="dea8c-156">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="dea8c-157">Basic256Sha256</span></span>|<span data-ttu-id="dea8c-158">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="dea8c-159">TripleDesSha256</span></span>|<span data-ttu-id="dea8c-160">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="dea8c-162">Użyj Aes128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="dea8c-164">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="dea8c-166">Użyj AES256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="dea8c-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="dea8c-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="dea8c-168">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dea8c-169">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dea8c-169">Child Elements</span></span>  
  
|<span data-ttu-id="dea8c-170">Element</span><span class="sxs-lookup"><span data-stu-id="dea8c-170">Element</span></span>|<span data-ttu-id="dea8c-171">Opis</span><span class="sxs-lookup"><span data-stu-id="dea8c-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dea8c-172">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="dea8c-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="dea8c-173">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="dea8c-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="dea8c-174">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="dea8c-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="dea8c-175">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="dea8c-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="dea8c-176">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="dea8c-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="dea8c-177">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="dea8c-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="dea8c-178">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="dea8c-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="dea8c-179">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="dea8c-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="dea8c-180">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="dea8c-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="dea8c-181">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="dea8c-181">A collection of token request parameters.</span></span> <span data-ttu-id="dea8c-182">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="dea8c-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dea8c-183">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dea8c-183">Parent Elements</span></span>  
  
|<span data-ttu-id="dea8c-184">Element</span><span class="sxs-lookup"><span data-stu-id="dea8c-184">Element</span></span>|<span data-ttu-id="dea8c-185">Opis</span><span class="sxs-lookup"><span data-stu-id="dea8c-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dea8c-186">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="dea8c-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="dea8c-187">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="dea8c-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dea8c-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dea8c-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="dea8c-189">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="dea8c-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dea8c-190">Powiązania</span><span class="sxs-lookup"><span data-stu-id="dea8c-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dea8c-191">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="dea8c-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dea8c-192">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="dea8c-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dea8c-193">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="dea8c-193">\<binding></span></span>](../../../misc/binding.md)
