---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 37d935287fa7dfba640c39071295fd660f4db7c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160826"
---
# <a name="issuer"></a><span data-ttu-id="645f4-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="645f4-101">\<issuer></span></span>
<span data-ttu-id="645f4-102">Określa Usługa tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="645f4-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="645f4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="645f4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="645f4-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="645f4-104">\<bindings></span></span>  
<span data-ttu-id="645f4-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="645f4-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="645f4-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="645f4-106">\<binding></span></span>  
<span data-ttu-id="645f4-107">\<security></span><span class="sxs-lookup"><span data-stu-id="645f4-107">\<security></span></span>  
<span data-ttu-id="645f4-108">\<message></span><span class="sxs-lookup"><span data-stu-id="645f4-108">\<message></span></span>  
<span data-ttu-id="645f4-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="645f4-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="645f4-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="645f4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="645f4-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="645f4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="645f4-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="645f4-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="645f4-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="645f4-113">Attributes</span></span>  
  
|<span data-ttu-id="645f4-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="645f4-114">Attribute</span></span>|<span data-ttu-id="645f4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="645f4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="645f4-116">adres</span><span class="sxs-lookup"><span data-stu-id="645f4-116">address</span></span>|<span data-ttu-id="645f4-117">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="645f4-117">Required string.</span></span> <span data-ttu-id="645f4-118">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="645f4-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="645f4-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="645f4-119">Child Elements</span></span>  
  
|<span data-ttu-id="645f4-120">Element</span><span class="sxs-lookup"><span data-stu-id="645f4-120">Element</span></span>|<span data-ttu-id="645f4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="645f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="645f4-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="645f4-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="645f4-123">Kolekcja nagłówków adresowych dla punktów końcowych, które można utworzyć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="645f4-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="645f4-124">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="645f4-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="645f4-125">Podczas używania tokenu wystawionego, określa ustawienia, które umożliwiają klienta do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="645f4-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="645f4-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="645f4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="645f4-127">Element</span><span class="sxs-lookup"><span data-stu-id="645f4-127">Element</span></span>|<span data-ttu-id="645f4-128">Opis</span><span class="sxs-lookup"><span data-stu-id="645f4-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="645f4-129">\<message></span><span class="sxs-lookup"><span data-stu-id="645f4-129">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="645f4-130">Określa ustawienia zabezpieczenia na poziomie komunikatu [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="645f4-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="645f4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="645f4-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="645f4-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="645f4-132">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="645f4-133">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="645f4-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="645f4-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="645f4-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="645f4-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="645f4-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="645f4-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="645f4-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="645f4-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="645f4-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
