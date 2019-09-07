---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397920"
---
# <a name="issuer"></a><span data-ttu-id="397ef-101">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="397ef-101">\<issuer></span></span>
<span data-ttu-id="397ef-102">Określa usługę tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="397ef-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="397ef-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="397ef-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="397ef-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="397ef-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="397ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="397ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="397ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="397ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="397ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="397ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="397ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="397ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="397ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> komunikatu**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="397ef-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="397ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> wystawcy**</span><span class="sxs-lookup"><span data-stu-id="397ef-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="397ef-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="397ef-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="397ef-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="397ef-112">Attributes and Elements</span></span>  
 <span data-ttu-id="397ef-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="397ef-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="397ef-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="397ef-114">Attributes</span></span>  
  
|<span data-ttu-id="397ef-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="397ef-115">Attribute</span></span>|<span data-ttu-id="397ef-116">Opis</span><span class="sxs-lookup"><span data-stu-id="397ef-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="397ef-117">adres</span><span class="sxs-lookup"><span data-stu-id="397ef-117">address</span></span>|<span data-ttu-id="397ef-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="397ef-118">Required string.</span></span> <span data-ttu-id="397ef-119">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="397ef-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="397ef-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="397ef-120">Child Elements</span></span>  
  
|<span data-ttu-id="397ef-121">Element</span><span class="sxs-lookup"><span data-stu-id="397ef-121">Element</span></span>|<span data-ttu-id="397ef-122">Opis</span><span class="sxs-lookup"><span data-stu-id="397ef-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="397ef-123">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="397ef-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="397ef-124">Kolekcja nagłówków adresów dla punktów końcowych, które może utworzyć Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="397ef-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="397ef-125">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="397ef-125">\<identity></span></span>](identity.md)|<span data-ttu-id="397ef-126">W przypadku korzystania z wystawionego tokenu określa ustawienia, które umożliwiają klientowi uwierzytelnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="397ef-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="397ef-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="397ef-127">Parent Elements</span></span>  
  
|<span data-ttu-id="397ef-128">Element</span><span class="sxs-lookup"><span data-stu-id="397ef-128">Element</span></span>|<span data-ttu-id="397ef-129">Opis</span><span class="sxs-lookup"><span data-stu-id="397ef-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="397ef-130">\<message></span><span class="sxs-lookup"><span data-stu-id="397ef-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="397ef-131">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [ \<elementu WSFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="397ef-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="397ef-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="397ef-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="397ef-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="397ef-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="397ef-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="397ef-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="397ef-135">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="397ef-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="397ef-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="397ef-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="397ef-137">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="397ef-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="397ef-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="397ef-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
