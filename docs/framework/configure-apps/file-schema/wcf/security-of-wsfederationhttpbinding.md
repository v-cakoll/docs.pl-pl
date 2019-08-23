---
title: <security> dla <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 875ce7d548d59f32465da817e9e956217f346f60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936540"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="5a356-102">\<zabezpieczenia > \<WSFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5a356-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="5a356-103">Definiuje ustawienia [ \<zabezpieczeń > WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5a356-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="5a356-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a356-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a356-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="5a356-105">\<bindings></span></span>  
<span data-ttu-id="5a356-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="5a356-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="5a356-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="5a356-107">\<binding></span></span>  
<span data-ttu-id="5a356-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5a356-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a356-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a356-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a356-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a356-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a356-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a356-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a356-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a356-112">Attributes</span></span>  
  
|<span data-ttu-id="5a356-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5a356-113">Attribute</span></span>|<span data-ttu-id="5a356-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5a356-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a356-115">Tryb</span><span class="sxs-lookup"><span data-stu-id="5a356-115">Mode</span></span>|<span data-ttu-id="5a356-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5a356-116">Optional.</span></span> <span data-ttu-id="5a356-117">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="5a356-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="5a356-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="5a356-118">The default value is `Message`.</span></span> <span data-ttu-id="5a356-119">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5a356-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5a356-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="5a356-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="5a356-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="5a356-121">Value</span></span>|<span data-ttu-id="5a356-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5a356-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5a356-123">Brak</span><span class="sxs-lookup"><span data-stu-id="5a356-123">None</span></span>|<span data-ttu-id="5a356-124">Komunikat protokołu SOAP nie jest zabezpieczony podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="5a356-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="5a356-125">Message</span><span class="sxs-lookup"><span data-stu-id="5a356-125">Message</span></span>|<span data-ttu-id="5a356-126">Integralność, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5a356-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="5a356-127">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="5a356-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="5a356-128">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5a356-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="5a356-129">Uwierzytelnianie klienta opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego</span><span class="sxs-lookup"><span data-stu-id="5a356-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="5a356-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5a356-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="5a356-131">Uwierzytelnianie za pomocą protokołu HTTPS zapewnia integralność, poufność i serwer.</span><span class="sxs-lookup"><span data-stu-id="5a356-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="5a356-132">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5a356-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="5a356-133">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP i opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="5a356-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a356-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a356-134">Child Elements</span></span>  
  
|<span data-ttu-id="5a356-135">Element</span><span class="sxs-lookup"><span data-stu-id="5a356-135">Element</span></span>|<span data-ttu-id="5a356-136">Opis</span><span class="sxs-lookup"><span data-stu-id="5a356-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a356-137">\<message></span><span class="sxs-lookup"><span data-stu-id="5a356-137">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="5a356-138">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5a356-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="5a356-139">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="5a356-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a356-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a356-140">Parent Elements</span></span>  
  
|<span data-ttu-id="5a356-141">Element</span><span class="sxs-lookup"><span data-stu-id="5a356-141">Element</span></span>|<span data-ttu-id="5a356-142">Opis</span><span class="sxs-lookup"><span data-stu-id="5a356-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a356-143">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="5a356-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5a356-144">Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5a356-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a356-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a356-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="5a356-146">Instrukcje: Utwórz WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5a356-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="5a356-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="5a356-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5a356-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="5a356-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="5a356-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5a356-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5a356-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5a356-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5a356-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5a356-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5a356-152">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="5a356-152">\<binding></span></span>](../../../misc/binding.md)
