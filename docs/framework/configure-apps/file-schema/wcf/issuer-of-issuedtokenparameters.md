---
title: '&lt;issuer&gt; w &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 58fdd93eb4f69e48783873df26bf1c35a2a849e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539158"
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="b7f37-102">&lt;issuer&gt; w &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b7f37-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="b7f37-103">Określa Usługa tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="b7f37-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="b7f37-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b7f37-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b7f37-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b7f37-105">\<bindings></span></span>  
<span data-ttu-id="b7f37-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b7f37-106">\<customBinding></span></span>  
<span data-ttu-id="b7f37-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b7f37-107">\<binding></span></span>  
<span data-ttu-id="b7f37-108">\<security></span><span class="sxs-lookup"><span data-stu-id="b7f37-108">\<security></span></span>  
<span data-ttu-id="b7f37-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b7f37-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="b7f37-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="b7f37-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7f37-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7f37-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7f37-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b7f37-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b7f37-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b7f37-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7f37-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b7f37-114">Attributes</span></span>  
  
|<span data-ttu-id="b7f37-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b7f37-115">Attribute</span></span>|<span data-ttu-id="b7f37-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b7f37-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7f37-117">adres</span><span class="sxs-lookup"><span data-stu-id="b7f37-117">address</span></span>|<span data-ttu-id="b7f37-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="b7f37-118">Required string.</span></span> <span data-ttu-id="b7f37-119">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="b7f37-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7f37-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b7f37-120">Child Elements</span></span>  
  
|<span data-ttu-id="b7f37-121">Element</span><span class="sxs-lookup"><span data-stu-id="b7f37-121">Element</span></span>|<span data-ttu-id="b7f37-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b7f37-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7f37-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="b7f37-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b7f37-124">Kolekcja nagłówków adresowych dla punktów końcowych, które można utworzyć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b7f37-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="b7f37-125">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="b7f37-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b7f37-126">Podczas używania tokenu wystawionego, określa ustawienia, które umożliwiają klienta do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="b7f37-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7f37-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b7f37-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b7f37-128">Element</span><span class="sxs-lookup"><span data-stu-id="b7f37-128">Element</span></span>|<span data-ttu-id="b7f37-129">Opis</span><span class="sxs-lookup"><span data-stu-id="b7f37-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7f37-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="b7f37-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="b7f37-131">Określa bieżący wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="b7f37-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7f37-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7f37-132">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b7f37-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b7f37-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b7f37-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b7f37-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b7f37-135">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b7f37-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b7f37-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b7f37-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b7f37-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b7f37-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b7f37-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b7f37-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b7f37-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b7f37-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b7f37-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b7f37-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="b7f37-141">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b7f37-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b7f37-142">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="b7f37-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
