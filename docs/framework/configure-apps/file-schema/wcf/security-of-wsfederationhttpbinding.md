---
title: <security> dla <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736330"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="c7689-102">\<security> dla \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c7689-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="c7689-103">Definiuje ustawienia zabezpieczeń [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c7689-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="c7689-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7689-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7689-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7689-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c7689-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7689-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7689-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7689-107">Attributes</span></span>  
  
|<span data-ttu-id="c7689-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c7689-108">Attribute</span></span>|<span data-ttu-id="c7689-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c7689-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7689-110">Tryb</span><span class="sxs-lookup"><span data-stu-id="c7689-110">Mode</span></span>|<span data-ttu-id="c7689-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c7689-111">Optional.</span></span> <span data-ttu-id="c7689-112">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="c7689-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="c7689-113">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="c7689-113">The default value is `Message`.</span></span> <span data-ttu-id="c7689-114">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="c7689-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c7689-115">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="c7689-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="c7689-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="c7689-116">Value</span></span>|<span data-ttu-id="c7689-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c7689-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c7689-118">Brak</span><span class="sxs-lookup"><span data-stu-id="c7689-118">None</span></span>|<span data-ttu-id="c7689-119">Komunikat protokołu SOAP nie jest zabezpieczony podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="c7689-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="c7689-120">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c7689-120">Message</span></span>|<span data-ttu-id="c7689-121">Integralność, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c7689-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="c7689-122">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="c7689-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c7689-123">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c7689-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="c7689-124">Uwierzytelnianie klienta opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego</span><span class="sxs-lookup"><span data-stu-id="c7689-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="c7689-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c7689-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="c7689-126">Uwierzytelnianie za pomocą protokołu HTTPS zapewnia integralność, poufność i serwer.</span><span class="sxs-lookup"><span data-stu-id="c7689-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="c7689-127">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c7689-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="c7689-128">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP i opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="c7689-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7689-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7689-129">Child Elements</span></span>  
  
|<span data-ttu-id="c7689-130">Element</span><span class="sxs-lookup"><span data-stu-id="c7689-130">Element</span></span>|<span data-ttu-id="c7689-131">Opis</span><span class="sxs-lookup"><span data-stu-id="c7689-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c7689-132">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7689-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="c7689-133">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="c7689-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7689-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7689-134">Parent Elements</span></span>  
  
|<span data-ttu-id="c7689-135">Element</span><span class="sxs-lookup"><span data-stu-id="c7689-135">Element</span></span>|<span data-ttu-id="c7689-136">Opis</span><span class="sxs-lookup"><span data-stu-id="c7689-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c7689-137">Definiuje wszystkie możliwości powiązań [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c7689-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7689-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7689-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="c7689-139">Instrukcje: tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c7689-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c7689-140">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c7689-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c7689-141">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="c7689-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c7689-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c7689-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c7689-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c7689-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c7689-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c7689-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
