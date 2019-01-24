---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 22e30e0962ec8d2eb0f7e52f4db143fba9bbf703
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491561"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="d897d-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="d897d-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="d897d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d897d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d897d-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d897d-104">\<bindings></span></span>  
<span data-ttu-id="d897d-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d897d-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="d897d-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d897d-106">\<binding></span></span>  
<span data-ttu-id="d897d-107">\<security></span><span class="sxs-lookup"><span data-stu-id="d897d-107">\<security></span></span>  
<span data-ttu-id="d897d-108">\<message></span><span class="sxs-lookup"><span data-stu-id="d897d-108">\<message></span></span>  
<span data-ttu-id="d897d-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="d897d-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d897d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d897d-110">Syntax</span></span>  
  
```xml  
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
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d897d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d897d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d897d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d897d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d897d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d897d-113">Attributes</span></span>  
  
|<span data-ttu-id="d897d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d897d-114">Attribute</span></span>|<span data-ttu-id="d897d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d897d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d897d-116">adres</span><span class="sxs-lookup"><span data-stu-id="d897d-116">address</span></span>|<span data-ttu-id="d897d-117">Wymagane `string` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d897d-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="d897d-118">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d897d-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="d897d-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="d897d-119">The address must be an absolute URI.</span></span> <span data-ttu-id="d897d-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="d897d-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d897d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d897d-121">Child Elements</span></span>  
  
|<span data-ttu-id="d897d-122">Element</span><span class="sxs-lookup"><span data-stu-id="d897d-122">Element</span></span>|<span data-ttu-id="d897d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d897d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d897d-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="d897d-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="d897d-125">Kolekcję nagłówków adresowych.</span><span class="sxs-lookup"><span data-stu-id="d897d-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="d897d-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="d897d-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d897d-127">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="d897d-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d897d-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d897d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d897d-129">Element</span><span class="sxs-lookup"><span data-stu-id="d897d-129">Element</span></span>|<span data-ttu-id="d897d-130">Opis</span><span class="sxs-lookup"><span data-stu-id="d897d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d897d-131">\<message></span><span class="sxs-lookup"><span data-stu-id="d897d-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d897d-132">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d897d-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d897d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d897d-133">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="d897d-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="d897d-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d897d-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="d897d-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d897d-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d897d-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d897d-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="d897d-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
