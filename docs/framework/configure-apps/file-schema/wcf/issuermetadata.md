---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: c557bd903462ccf4029b7317cbd45610e3fba165
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264457"
---
# <a name="issuermetadata"></a><span data-ttu-id="e31ac-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="e31ac-101">\<issuerMetadata></span></span>
<span data-ttu-id="e31ac-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e31ac-102">\<system.serviceModel></span></span>  
<span data-ttu-id="e31ac-103">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e31ac-103">\<bindings></span></span>  
<span data-ttu-id="e31ac-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e31ac-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="e31ac-105">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e31ac-105">\<binding></span></span>  
<span data-ttu-id="e31ac-106">\<security></span><span class="sxs-lookup"><span data-stu-id="e31ac-106">\<security></span></span>  
<span data-ttu-id="e31ac-107">\<message></span><span class="sxs-lookup"><span data-stu-id="e31ac-107">\<message></span></span>  
<span data-ttu-id="e31ac-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="e31ac-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31ac-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e31ac-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e31ac-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e31ac-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e31ac-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e31ac-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e31ac-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e31ac-112">Attributes</span></span>  
  
|<span data-ttu-id="e31ac-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e31ac-113">Attribute</span></span>|<span data-ttu-id="e31ac-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e31ac-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e31ac-115">adres</span><span class="sxs-lookup"><span data-stu-id="e31ac-115">address</span></span>|<span data-ttu-id="e31ac-116">Wymagane `string` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e31ac-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="e31ac-117">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e31ac-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="e31ac-118">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="e31ac-118">The address must be an absolute URI.</span></span> <span data-ttu-id="e31ac-119">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e31ac-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e31ac-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e31ac-120">Child Elements</span></span>  
  
|<span data-ttu-id="e31ac-121">Element</span><span class="sxs-lookup"><span data-stu-id="e31ac-121">Element</span></span>|<span data-ttu-id="e31ac-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e31ac-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e31ac-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="e31ac-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="e31ac-124">Kolekcję nagłówków adresowych.</span><span class="sxs-lookup"><span data-stu-id="e31ac-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="e31ac-125">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="e31ac-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e31ac-126">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="e31ac-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e31ac-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e31ac-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e31ac-128">Element</span><span class="sxs-lookup"><span data-stu-id="e31ac-128">Element</span></span>|<span data-ttu-id="e31ac-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e31ac-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e31ac-130">\<message></span><span class="sxs-lookup"><span data-stu-id="e31ac-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="e31ac-131">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e31ac-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e31ac-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e31ac-132">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="e31ac-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="e31ac-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e31ac-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e31ac-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e31ac-135">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e31ac-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e31ac-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="e31ac-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
