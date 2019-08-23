---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929373"
---
# <a name="issuer"></a><span data-ttu-id="2117a-101">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="2117a-101">\<issuer></span></span>
<span data-ttu-id="2117a-102">Określa usługę tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="2117a-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="2117a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2117a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2117a-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="2117a-104">\<bindings></span></span>  
<span data-ttu-id="2117a-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2117a-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="2117a-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="2117a-106">\<binding></span></span>  
<span data-ttu-id="2117a-107">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2117a-107">\<security></span></span>  
<span data-ttu-id="2117a-108">\<message></span><span class="sxs-lookup"><span data-stu-id="2117a-108">\<message></span></span>  
<span data-ttu-id="2117a-109">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="2117a-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2117a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2117a-110">Syntax</span></span>  
  
```xml  
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
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2117a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2117a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2117a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2117a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2117a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2117a-113">Attributes</span></span>  
  
|<span data-ttu-id="2117a-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2117a-114">Attribute</span></span>|<span data-ttu-id="2117a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2117a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2117a-116">adres</span><span class="sxs-lookup"><span data-stu-id="2117a-116">address</span></span>|<span data-ttu-id="2117a-117">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="2117a-117">Required string.</span></span> <span data-ttu-id="2117a-118">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="2117a-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2117a-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2117a-119">Child Elements</span></span>  
  
|<span data-ttu-id="2117a-120">Element</span><span class="sxs-lookup"><span data-stu-id="2117a-120">Element</span></span>|<span data-ttu-id="2117a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2117a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2117a-122">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="2117a-122">\<headers></span></span>](headers-element.md)|<span data-ttu-id="2117a-123">Kolekcja nagłówków adresów dla punktów końcowych, które może utworzyć Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2117a-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="2117a-124">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="2117a-124">\<identity></span></span>](identity.md)|<span data-ttu-id="2117a-125">W przypadku korzystania z wystawionego tokenu określa ustawienia, które umożliwiają klientowi uwierzytelnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="2117a-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2117a-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2117a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2117a-127">Element</span><span class="sxs-lookup"><span data-stu-id="2117a-127">Element</span></span>|<span data-ttu-id="2117a-128">Opis</span><span class="sxs-lookup"><span data-stu-id="2117a-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2117a-129">\<message></span><span class="sxs-lookup"><span data-stu-id="2117a-129">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="2117a-130">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<elementu WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2117a-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2117a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2117a-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="2117a-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="2117a-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2117a-133">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2117a-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2117a-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="2117a-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2117a-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2117a-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2117a-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="2117a-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="2117a-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2117a-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
