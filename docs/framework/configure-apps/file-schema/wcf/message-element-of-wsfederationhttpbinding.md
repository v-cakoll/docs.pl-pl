---
title: <message>elementu<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738981"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="328ed-102">\<message>elementu\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="328ed-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="328ed-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="328ed-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="328ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="328ed-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="328ed-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="328ed-105">Attributes and Elements</span></span>  
 <span data-ttu-id="328ed-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="328ed-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="328ed-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="328ed-107">Attributes</span></span>  
  
|<span data-ttu-id="328ed-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="328ed-108">Attribute</span></span>|<span data-ttu-id="328ed-109">Opis</span><span class="sxs-lookup"><span data-stu-id="328ed-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="328ed-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="328ed-110">algorithmSuite</span></span>|<span data-ttu-id="328ed-111">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="328ed-112">Zobacz tabelę "atrybut algorithmSuite", aby uzyskać prawidłowe wartości tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="328ed-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="328ed-113">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="328ed-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="328ed-114">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="328ed-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="328ed-115">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="328ed-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="328ed-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="328ed-116">issuedKeyType</span></span>|<span data-ttu-id="328ed-117">Określa typ klucza do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="328ed-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="328ed-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="328ed-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="328ed-119">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="328ed-119">-   SymmetricKey</span></span><br /><span data-ttu-id="328ed-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="328ed-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="328ed-121">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="328ed-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="328ed-122">Ten atrybut jest typu <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="328ed-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="328ed-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="328ed-123">issuedTokenType</span></span>|<span data-ttu-id="328ed-124">Ciąg zawierający identyfikator URI, który określa typ tokenu do wystawienia.</span><span class="sxs-lookup"><span data-stu-id="328ed-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="328ed-125">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="328ed-125">The default is `null`.</span></span>|  
|<span data-ttu-id="328ed-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="328ed-126">negotiateServiceCredential</span></span>|<span data-ttu-id="328ed-127">Wartość logiczna określająca, czy poświadczenie usługi powinno być wymieniane jako część negocjacji lub jest dostępne poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="328ed-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="328ed-128">Wartość domyślna to `true` , co oznacza, że poświadczenie usługi jest negocjowane.</span><span class="sxs-lookup"><span data-stu-id="328ed-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="328ed-129">algorithmSuite — atrybut</span><span class="sxs-lookup"><span data-stu-id="328ed-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="328ed-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="328ed-130">Value</span></span>|<span data-ttu-id="328ed-131">Opis</span><span class="sxs-lookup"><span data-stu-id="328ed-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="328ed-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="328ed-132">Basic128</span></span>|<span data-ttu-id="328ed-133">Użyj szyfrowania Basic128, SHA1 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="328ed-134">Basic192</span></span>|<span data-ttu-id="328ed-135">Użyj szyfrowania Basic192, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="328ed-136">Basic256</span></span>|<span data-ttu-id="328ed-137">Użyj szyfrowania Basic256, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-138">Basic256Rsa15</span></span>|<span data-ttu-id="328ed-139">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-140">Basic192Rsa15</span></span>|<span data-ttu-id="328ed-141">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="328ed-142">TripleDes</span></span>|<span data-ttu-id="328ed-143">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości, RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-144">Basic128Rsa15</span></span>|<span data-ttu-id="328ed-145">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-146">TripleDesRsa15</span></span>|<span data-ttu-id="328ed-147">Użyj szyfrowania TripleDes, SHA1 dla skrótu wiadomości i Rsa15 do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="328ed-148">Basic128Sha256</span></span>|<span data-ttu-id="328ed-149">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="328ed-150">Basic192Sha256</span></span>|<span data-ttu-id="328ed-151">Użyj Basic192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="328ed-152">Basic256Sha256</span></span>|<span data-ttu-id="328ed-153">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="328ed-154">TripleDesSha256</span></span>|<span data-ttu-id="328ed-155">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i RSA-OAEP-mgf1p do zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="328ed-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="328ed-157">Użyj Basic128 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="328ed-159">Użyj Aes192 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="328ed-161">Użyj Basic256 na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="328ed-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="328ed-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="328ed-163">Użyj TripleDes na potrzeby szyfrowania wiadomości, SHA256 dla skrótu wiadomości i Rsa15 dla zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="328ed-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="328ed-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="328ed-164">Child Elements</span></span>  
  
|<span data-ttu-id="328ed-165">Element</span><span class="sxs-lookup"><span data-stu-id="328ed-165">Element</span></span>|<span data-ttu-id="328ed-166">Opis</span><span class="sxs-lookup"><span data-stu-id="328ed-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="328ed-167">Określa kolekcję typów roszczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="328ed-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="328ed-168">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="328ed-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="328ed-169">issuer</span><span class="sxs-lookup"><span data-stu-id="328ed-169">issuer</span></span>|<span data-ttu-id="328ed-170">Określa punkt końcowy, który wystawia token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="328ed-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="328ed-171">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="328ed-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="328ed-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="328ed-172">issuerMetadata</span></span>|<span data-ttu-id="328ed-173">Określa adres punktu końcowego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="328ed-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="328ed-174">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="328ed-174">A collection of token request parameters.</span></span> <span data-ttu-id="328ed-175">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="328ed-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="328ed-176">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="328ed-176">Parent Elements</span></span>  
  
|<span data-ttu-id="328ed-177">Element</span><span class="sxs-lookup"><span data-stu-id="328ed-177">Element</span></span>|<span data-ttu-id="328ed-178">Opis</span><span class="sxs-lookup"><span data-stu-id="328ed-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="328ed-179">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="328ed-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="328ed-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="328ed-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="328ed-181">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="328ed-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="328ed-182">Powiązania</span><span class="sxs-lookup"><span data-stu-id="328ed-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="328ed-183">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="328ed-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="328ed-184">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="328ed-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
