---
title: <issuer> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397943"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="33066-102">\<issuer> dla \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="33066-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="33066-103">Określa usługę tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="33066-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="33066-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33066-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33066-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="33066-105">Attributes and Elements</span></span>  
 <span data-ttu-id="33066-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="33066-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33066-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="33066-107">Attributes</span></span>  
  
|<span data-ttu-id="33066-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="33066-108">Attribute</span></span>|<span data-ttu-id="33066-109">Opis</span><span class="sxs-lookup"><span data-stu-id="33066-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33066-110">adres</span><span class="sxs-lookup"><span data-stu-id="33066-110">address</span></span>|<span data-ttu-id="33066-111">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="33066-111">Required string.</span></span> <span data-ttu-id="33066-112">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="33066-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33066-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="33066-113">Child Elements</span></span>  
  
|<span data-ttu-id="33066-114">Element</span><span class="sxs-lookup"><span data-stu-id="33066-114">Element</span></span>|<span data-ttu-id="33066-115">Opis</span><span class="sxs-lookup"><span data-stu-id="33066-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="33066-116">Kolekcja nagłówków adresów dla punktów końcowych, które może utworzyć Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="33066-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="33066-117">W przypadku korzystania z wystawionego tokenu określa ustawienia, które umożliwiają klientowi uwierzytelnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="33066-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33066-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="33066-118">Parent Elements</span></span>  
  
|<span data-ttu-id="33066-119">Element</span><span class="sxs-lookup"><span data-stu-id="33066-119">Element</span></span>|<span data-ttu-id="33066-120">Opis</span><span class="sxs-lookup"><span data-stu-id="33066-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="33066-121">Określa bieżący token wystawiony.</span><span class="sxs-lookup"><span data-stu-id="33066-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33066-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33066-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="33066-123">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="33066-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="33066-124">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="33066-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="33066-125">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="33066-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="33066-126">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="33066-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="33066-127">Powiązania</span><span class="sxs-lookup"><span data-stu-id="33066-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="33066-128">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="33066-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="33066-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="33066-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="33066-130">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="33066-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="33066-131">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="33066-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
