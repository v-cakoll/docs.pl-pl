---
title: <message>elementu<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: e26e1f94fb38e0654fd0bc9f06c6096a488bccfe
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400282"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="3e8b8-102">\<komunikat > elementu \<WSFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3e8b8-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="3e8b8-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<> WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3e8b8-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="3e8b8-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e8b8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e8b8-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3e8b8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3e8b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3e8b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3e8b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3e8b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3e8b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="3e8b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3e8b8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3e8b8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3e8b8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> komunikatu**</span><span class="sxs-lookup"><span data-stu-id="3e8b8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8b8-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e8b8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e8b8-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e8b8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3e8b8-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e8b8-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e8b8-114">Attributes</span></span>  
  
|<span data-ttu-id="3e8b8-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e8b8-115">Attribute</span></span>|<span data-ttu-id="3e8b8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3e8b8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e8b8-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="3e8b8-117">algorithmSuite</span></span>|<span data-ttu-id="3e8b8-118">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="3e8b8-119">Zobacz tabelę "atrybut algorithmSuite", aby uzyskać prawidłowe wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="3e8b8-120">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="3e8b8-121">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="3e8b8-122">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="3e8b8-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="3e8b8-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="3e8b8-123">issuedKeyType</span></span>|<span data-ttu-id="3e8b8-124">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="3e8b8-125">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="3e8b8-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3e8b8-126">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="3e8b8-126">-   SymmetricKey</span></span><br /><span data-ttu-id="3e8b8-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="3e8b8-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="3e8b8-128">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="3e8b8-129">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="3e8b8-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="3e8b8-130">issuedTokenType</span></span>|<span data-ttu-id="3e8b8-131">Ciąg zawierający identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="3e8b8-132">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-132">The default is `null`.</span></span>|  
|<span data-ttu-id="3e8b8-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="3e8b8-133">negotiateServiceCredential</span></span>|<span data-ttu-id="3e8b8-134">Wartość logiczna określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji lub jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="3e8b8-135">Wartość domyślna to `true`, co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="3e8b8-136">algorithmSuite Attribute</span><span class="sxs-lookup"><span data-stu-id="3e8b8-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="3e8b8-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="3e8b8-137">Value</span></span>|<span data-ttu-id="3e8b8-138">Opis</span><span class="sxs-lookup"><span data-stu-id="3e8b8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e8b8-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="3e8b8-139">Basic128</span></span>|<span data-ttu-id="3e8b8-140">Użyj szyfrowania Basic128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="3e8b8-141">Basic192</span></span>|<span data-ttu-id="3e8b8-142">Użyj szyfrowania Basic192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="3e8b8-143">Basic256</span></span>|<span data-ttu-id="3e8b8-144">Użyj szyfrowania Basic256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-145">Basic256Rsa15</span></span>|<span data-ttu-id="3e8b8-146">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-147">Basic192Rsa15</span></span>|<span data-ttu-id="3e8b8-148">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="3e8b8-149">TripleDes</span></span>|<span data-ttu-id="3e8b8-150">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-151">Basic128Rsa15</span></span>|<span data-ttu-id="3e8b8-152">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-153">TripleDesRsa15</span></span>|<span data-ttu-id="3e8b8-154">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="3e8b8-155">Basic128Sha256</span></span>|<span data-ttu-id="3e8b8-156">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="3e8b8-157">Basic192Sha256</span></span>|<span data-ttu-id="3e8b8-158">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="3e8b8-159">Basic256Sha256</span></span>|<span data-ttu-id="3e8b8-160">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="3e8b8-161">TripleDesSha256</span></span>|<span data-ttu-id="3e8b8-162">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="3e8b8-164">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="3e8b8-166">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="3e8b8-168">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3e8b8-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3e8b8-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="3e8b8-170">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e8b8-171">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e8b8-171">Child Elements</span></span>  
  
|<span data-ttu-id="3e8b8-172">Element</span><span class="sxs-lookup"><span data-stu-id="3e8b8-172">Element</span></span>|<span data-ttu-id="3e8b8-173">Opis</span><span class="sxs-lookup"><span data-stu-id="3e8b8-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e8b8-174">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="3e8b8-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="3e8b8-175">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="3e8b8-176">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="3e8b8-177">issuer</span><span class="sxs-lookup"><span data-stu-id="3e8b8-177">issuer</span></span>|<span data-ttu-id="3e8b8-178">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="3e8b8-179">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="3e8b8-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="3e8b8-180">issuerMetadata</span></span>|<span data-ttu-id="3e8b8-181">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="3e8b8-182">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="3e8b8-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="3e8b8-183">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-183">A collection of token request parameters.</span></span> <span data-ttu-id="3e8b8-184">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e8b8-185">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e8b8-185">Parent Elements</span></span>  
  
|<span data-ttu-id="3e8b8-186">Element</span><span class="sxs-lookup"><span data-stu-id="3e8b8-186">Element</span></span>|<span data-ttu-id="3e8b8-187">Opis</span><span class="sxs-lookup"><span data-stu-id="3e8b8-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e8b8-188">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="3e8b8-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="3e8b8-189">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e8b8-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e8b8-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e8b8-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="3e8b8-191">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3e8b8-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3e8b8-192">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3e8b8-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3e8b8-193">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="3e8b8-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3e8b8-194">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="3e8b8-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3e8b8-195">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="3e8b8-195">\<binding></span></span>](../../../misc/binding.md)
