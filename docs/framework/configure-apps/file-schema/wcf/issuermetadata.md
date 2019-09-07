---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397891"
---
# <a name="issuermetadata"></a><span data-ttu-id="cc1af-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="cc1af-101">\<issuerMetadata></span></span>

<span data-ttu-id="cc1af-102">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc1af-102">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc1af-103">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cc1af-103">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cc1af-104">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="cc1af-104">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cc1af-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="cc1af-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="cc1af-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="cc1af-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="cc1af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="cc1af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="cc1af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> komunikatu**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="cc1af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="cc1af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="cc1af-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1af-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc1af-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc1af-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cc1af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc1af-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cc1af-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc1af-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc1af-113">Attributes</span></span>  
  
|<span data-ttu-id="cc1af-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cc1af-114">Attribute</span></span>|<span data-ttu-id="cc1af-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cc1af-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc1af-116">adres</span><span class="sxs-lookup"><span data-stu-id="cc1af-116">address</span></span>|<span data-ttu-id="cc1af-117">Wymagany `string` atrybut.</span><span class="sxs-lookup"><span data-stu-id="cc1af-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="cc1af-118">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cc1af-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="cc1af-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="cc1af-119">The address must be an absolute URI.</span></span> <span data-ttu-id="cc1af-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="cc1af-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc1af-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc1af-121">Child Elements</span></span>  
  
|<span data-ttu-id="cc1af-122">Element</span><span class="sxs-lookup"><span data-stu-id="cc1af-122">Element</span></span>|<span data-ttu-id="cc1af-123">Opis</span><span class="sxs-lookup"><span data-stu-id="cc1af-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc1af-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="cc1af-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="cc1af-125">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="cc1af-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="cc1af-126">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="cc1af-126">\<identity></span></span>](identity.md)|<span data-ttu-id="cc1af-127">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="cc1af-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc1af-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cc1af-128">Parent Elements</span></span>  
  
|<span data-ttu-id="cc1af-129">Element</span><span class="sxs-lookup"><span data-stu-id="cc1af-129">Element</span></span>|<span data-ttu-id="cc1af-130">Opis</span><span class="sxs-lookup"><span data-stu-id="cc1af-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc1af-131">\<message></span><span class="sxs-lookup"><span data-stu-id="cc1af-131">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="cc1af-132">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<elementu WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="cc1af-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc1af-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc1af-133">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="cc1af-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="cc1af-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cc1af-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="cc1af-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="cc1af-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="cc1af-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="cc1af-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="cc1af-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
