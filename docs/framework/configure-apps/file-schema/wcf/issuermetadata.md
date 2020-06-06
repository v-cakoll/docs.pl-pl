---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397891"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="b388b-101">Składnia</span><span class="sxs-lookup"><span data-stu-id="b388b-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b388b-102">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b388b-102">Attributes and Elements</span></span>  
 <span data-ttu-id="b388b-103">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b388b-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b388b-104">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b388b-104">Attributes</span></span>  
  
|<span data-ttu-id="b388b-105">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b388b-105">Attribute</span></span>|<span data-ttu-id="b388b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b388b-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b388b-107">adres</span><span class="sxs-lookup"><span data-stu-id="b388b-107">address</span></span>|<span data-ttu-id="b388b-108">Wymagany `string` atrybut.</span><span class="sxs-lookup"><span data-stu-id="b388b-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="b388b-109">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b388b-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="b388b-110">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="b388b-110">The address must be an absolute URI.</span></span> <span data-ttu-id="b388b-111">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="b388b-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b388b-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b388b-112">Child Elements</span></span>  
  
|<span data-ttu-id="b388b-113">Element</span><span class="sxs-lookup"><span data-stu-id="b388b-113">Element</span></span>|<span data-ttu-id="b388b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b388b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="b388b-115">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="b388b-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="b388b-116">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="b388b-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b388b-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b388b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b388b-118">Element</span><span class="sxs-lookup"><span data-stu-id="b388b-118">Element</span></span>|<span data-ttu-id="b388b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b388b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="b388b-120">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b388b-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b388b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b388b-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="b388b-122">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b388b-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b388b-123">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b388b-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b388b-124">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b388b-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b388b-125">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b388b-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
