---
title: <issuer> z <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113545"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="c2826-102">\<Wystawca > z \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c2826-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="c2826-103">Określa Usługa tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="c2826-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="c2826-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c2826-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c2826-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c2826-105">\<bindings></span></span>  
<span data-ttu-id="c2826-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c2826-106">\<customBinding></span></span>  
<span data-ttu-id="c2826-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c2826-107">\<binding></span></span>  
<span data-ttu-id="c2826-108">\<security></span><span class="sxs-lookup"><span data-stu-id="c2826-108">\<security></span></span>  
<span data-ttu-id="c2826-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c2826-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="c2826-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="c2826-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2826-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2826-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2826-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2826-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c2826-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2826-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2826-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2826-114">Attributes</span></span>  
  
|<span data-ttu-id="c2826-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2826-115">Attribute</span></span>|<span data-ttu-id="c2826-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c2826-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2826-117">adres</span><span class="sxs-lookup"><span data-stu-id="c2826-117">address</span></span>|<span data-ttu-id="c2826-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="c2826-118">Required string.</span></span> <span data-ttu-id="c2826-119">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="c2826-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2826-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2826-120">Child Elements</span></span>  
  
|<span data-ttu-id="c2826-121">Element</span><span class="sxs-lookup"><span data-stu-id="c2826-121">Element</span></span>|<span data-ttu-id="c2826-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c2826-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2826-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="c2826-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="c2826-124">Kolekcja nagłówków adresowych dla punktów końcowych, które można utworzyć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c2826-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="c2826-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="c2826-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c2826-126">Podczas używania tokenu wystawionego, określa ustawienia, które umożliwiają klienta do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="c2826-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2826-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2826-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c2826-128">Element</span><span class="sxs-lookup"><span data-stu-id="c2826-128">Element</span></span>|<span data-ttu-id="c2826-129">Opis</span><span class="sxs-lookup"><span data-stu-id="c2826-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2826-130">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="c2826-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="c2826-131">Określa bieżący wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="c2826-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2826-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2826-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c2826-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="c2826-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c2826-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="c2826-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c2826-135">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c2826-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c2826-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="c2826-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c2826-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c2826-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c2826-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c2826-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c2826-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c2826-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c2826-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c2826-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="c2826-141">Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c2826-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c2826-142">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="c2826-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
