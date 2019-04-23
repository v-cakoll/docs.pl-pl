---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 0dffad6a17720dd0506acbcd60efe4aafe24ed28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090111"
---
# <a name="issuermetadata"></a><span data-ttu-id="a588d-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a588d-101">\<issuerMetadata></span></span>
<span data-ttu-id="a588d-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a588d-102">\<system.serviceModel></span></span>  
<span data-ttu-id="a588d-103">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a588d-103">\<bindings></span></span>  
<span data-ttu-id="a588d-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a588d-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="a588d-105">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a588d-105">\<binding></span></span>  
<span data-ttu-id="a588d-106">\<security></span><span class="sxs-lookup"><span data-stu-id="a588d-106">\<security></span></span>  
<span data-ttu-id="a588d-107">\<message></span><span class="sxs-lookup"><span data-stu-id="a588d-107">\<message></span></span>  
<span data-ttu-id="a588d-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a588d-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a588d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a588d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a588d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a588d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a588d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a588d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a588d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a588d-112">Attributes</span></span>  
  
|<span data-ttu-id="a588d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a588d-113">Attribute</span></span>|<span data-ttu-id="a588d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a588d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a588d-115">adres</span><span class="sxs-lookup"><span data-stu-id="a588d-115">address</span></span>|<span data-ttu-id="a588d-116">Wymagane `string` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a588d-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="a588d-117">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a588d-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="a588d-118">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="a588d-118">The address must be an absolute URI.</span></span> <span data-ttu-id="a588d-119">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="a588d-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a588d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a588d-120">Child Elements</span></span>  
  
|<span data-ttu-id="a588d-121">Element</span><span class="sxs-lookup"><span data-stu-id="a588d-121">Element</span></span>|<span data-ttu-id="a588d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a588d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a588d-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="a588d-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="a588d-124">Kolekcję nagłówków adresowych.</span><span class="sxs-lookup"><span data-stu-id="a588d-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="a588d-125">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="a588d-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a588d-126">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="a588d-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a588d-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a588d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a588d-128">Element</span><span class="sxs-lookup"><span data-stu-id="a588d-128">Element</span></span>|<span data-ttu-id="a588d-129">Opis</span><span class="sxs-lookup"><span data-stu-id="a588d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a588d-130">\<message></span><span class="sxs-lookup"><span data-stu-id="a588d-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a588d-131">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a588d-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a588d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a588d-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="a588d-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a588d-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a588d-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a588d-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a588d-135">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a588d-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a588d-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a588d-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
