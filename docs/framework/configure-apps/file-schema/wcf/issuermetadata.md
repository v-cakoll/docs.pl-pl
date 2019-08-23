---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: bf512c427637ca65a7271ec8300a373a38632108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913520"
---
# <a name="issuermetadata"></a><span data-ttu-id="c122e-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="c122e-101">\<issuerMetadata></span></span>
<span data-ttu-id="c122e-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c122e-102">\<system.serviceModel></span></span>  
<span data-ttu-id="c122e-103">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="c122e-103">\<bindings></span></span>  
<span data-ttu-id="c122e-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c122e-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="c122e-105">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="c122e-105">\<binding></span></span>  
<span data-ttu-id="c122e-106">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c122e-106">\<security></span></span>  
<span data-ttu-id="c122e-107">\<message></span><span class="sxs-lookup"><span data-stu-id="c122e-107">\<message></span></span>  
<span data-ttu-id="c122e-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="c122e-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c122e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c122e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c122e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c122e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c122e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c122e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c122e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c122e-112">Attributes</span></span>  
  
|<span data-ttu-id="c122e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c122e-113">Attribute</span></span>|<span data-ttu-id="c122e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c122e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c122e-115">adres</span><span class="sxs-lookup"><span data-stu-id="c122e-115">address</span></span>|<span data-ttu-id="c122e-116">Wymagany `string` atrybut.</span><span class="sxs-lookup"><span data-stu-id="c122e-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="c122e-117">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c122e-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="c122e-118">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="c122e-118">The address must be an absolute URI.</span></span> <span data-ttu-id="c122e-119">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="c122e-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c122e-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c122e-120">Child Elements</span></span>  
  
|<span data-ttu-id="c122e-121">Element</span><span class="sxs-lookup"><span data-stu-id="c122e-121">Element</span></span>|<span data-ttu-id="c122e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c122e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c122e-123">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="c122e-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="c122e-124">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="c122e-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="c122e-125">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="c122e-125">\<identity></span></span>](identity.md)|<span data-ttu-id="c122e-126">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="c122e-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c122e-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c122e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c122e-128">Element</span><span class="sxs-lookup"><span data-stu-id="c122e-128">Element</span></span>|<span data-ttu-id="c122e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="c122e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c122e-130">\<message></span><span class="sxs-lookup"><span data-stu-id="c122e-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c122e-131">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<elementu WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c122e-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c122e-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c122e-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="c122e-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="c122e-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c122e-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="c122e-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c122e-135">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c122e-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c122e-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="c122e-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
