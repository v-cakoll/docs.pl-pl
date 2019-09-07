---
title: <security> dla <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 6c07d1ca18837f66548411262b84b9a326f5ec4a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399731"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="e6343-102">\<zabezpieczenia > \<WSFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e6343-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="e6343-103">Definiuje ustawienia [ \<zabezpieczeń > WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e6343-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="e6343-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6343-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6343-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e6343-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6343-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e6343-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e6343-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e6343-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e6343-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="e6343-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e6343-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="e6343-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6343-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6343-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6343-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6343-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e6343-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6343-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6343-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6343-113">Attributes</span></span>  
  
|<span data-ttu-id="e6343-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6343-114">Attribute</span></span>|<span data-ttu-id="e6343-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e6343-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6343-116">Tryb</span><span class="sxs-lookup"><span data-stu-id="e6343-116">Mode</span></span>|<span data-ttu-id="e6343-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e6343-117">Optional.</span></span> <span data-ttu-id="e6343-118">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="e6343-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e6343-119">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="e6343-119">The default value is `Message`.</span></span> <span data-ttu-id="e6343-120">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e6343-120">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e6343-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="e6343-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="e6343-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="e6343-122">Value</span></span>|<span data-ttu-id="e6343-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e6343-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6343-124">Brak</span><span class="sxs-lookup"><span data-stu-id="e6343-124">None</span></span>|<span data-ttu-id="e6343-125">Komunikat protokołu SOAP nie jest zabezpieczony podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="e6343-125">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="e6343-126">Message</span><span class="sxs-lookup"><span data-stu-id="e6343-126">Message</span></span>|<span data-ttu-id="e6343-127">Integralność, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e6343-127">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="e6343-128">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="e6343-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="e6343-129">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e6343-129">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="e6343-130">Uwierzytelnianie klienta opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego</span><span class="sxs-lookup"><span data-stu-id="e6343-130">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="e6343-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e6343-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="e6343-132">Uwierzytelnianie za pomocą protokołu HTTPS zapewnia integralność, poufność i serwer.</span><span class="sxs-lookup"><span data-stu-id="e6343-132">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="e6343-133">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e6343-133">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="e6343-134">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP i opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="e6343-134">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6343-135">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6343-135">Child Elements</span></span>  
  
|<span data-ttu-id="e6343-136">Element</span><span class="sxs-lookup"><span data-stu-id="e6343-136">Element</span></span>|<span data-ttu-id="e6343-137">Opis</span><span class="sxs-lookup"><span data-stu-id="e6343-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6343-138">\<message></span><span class="sxs-lookup"><span data-stu-id="e6343-138">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="e6343-139">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e6343-139">Defines the settings for the message-level security.</span></span> <span data-ttu-id="e6343-140">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="e6343-140">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6343-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6343-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e6343-142">Element</span><span class="sxs-lookup"><span data-stu-id="e6343-142">Element</span></span>|<span data-ttu-id="e6343-143">Opis</span><span class="sxs-lookup"><span data-stu-id="e6343-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6343-144">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="e6343-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e6343-145">Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e6343-145">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6343-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6343-146">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="e6343-147">Instrukcje: Utwórz WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e6343-147">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="e6343-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e6343-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e6343-149">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="e6343-149">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="e6343-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e6343-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6343-151">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e6343-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e6343-152">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e6343-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e6343-153">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="e6343-153">\<binding></span></span>](../../../misc/binding.md)
