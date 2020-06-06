---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397920"
---
# \<issuer>
<span data-ttu-id="a2557-101">Określa usługę tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="a2557-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="a2557-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2557-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2557-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a2557-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a2557-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a2557-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2557-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2557-105">Attributes</span></span>  
  
|<span data-ttu-id="a2557-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a2557-106">Attribute</span></span>|<span data-ttu-id="a2557-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a2557-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2557-108">adres</span><span class="sxs-lookup"><span data-stu-id="a2557-108">address</span></span>|<span data-ttu-id="a2557-109">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="a2557-109">Required string.</span></span> <span data-ttu-id="a2557-110">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="a2557-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2557-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2557-111">Child Elements</span></span>  
  
|<span data-ttu-id="a2557-112">Element</span><span class="sxs-lookup"><span data-stu-id="a2557-112">Element</span></span>|<span data-ttu-id="a2557-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a2557-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="a2557-114">Kolekcja nagłówków adresów dla punktów końcowych, które może utworzyć Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a2557-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="a2557-115">W przypadku korzystania z wystawionego tokenu określa ustawienia, które umożliwiają klientowi uwierzytelnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="a2557-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2557-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2557-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a2557-117">Element</span><span class="sxs-lookup"><span data-stu-id="a2557-117">Element</span></span>|<span data-ttu-id="a2557-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a2557-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a2557-119">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a2557-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2557-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2557-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="a2557-121">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a2557-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a2557-122">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a2557-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a2557-123">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a2557-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a2557-124">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a2557-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a2557-125">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a2557-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a2557-126">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a2557-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
