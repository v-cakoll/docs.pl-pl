---
title: '&lt;issuer&gt; w &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1eae3b472e33d4d0504ba487c8c871165af8cdf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="b036d-102">&lt;issuer&gt; w &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b036d-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="b036d-103">Określa zabezpieczeń tokenu usługi (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="b036d-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="b036d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b036d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b036d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b036d-105">\<bindings></span></span>  
<span data-ttu-id="b036d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b036d-106">\<customBinding></span></span>  
<span data-ttu-id="b036d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b036d-107">\<binding></span></span>  
<span data-ttu-id="b036d-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="b036d-108">\<security></span></span>  
<span data-ttu-id="b036d-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b036d-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="b036d-110">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="b036d-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b036d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b036d-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b036d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b036d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b036d-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b036d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b036d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b036d-114">Attributes</span></span>  
  
|<span data-ttu-id="b036d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b036d-115">Attribute</span></span>|<span data-ttu-id="b036d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b036d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b036d-117">adres</span><span class="sxs-lookup"><span data-stu-id="b036d-117">address</span></span>|<span data-ttu-id="b036d-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="b036d-118">Required string.</span></span> <span data-ttu-id="b036d-119">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="b036d-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b036d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b036d-120">Child Elements</span></span>  
  
|<span data-ttu-id="b036d-121">Element</span><span class="sxs-lookup"><span data-stu-id="b036d-121">Element</span></span>|<span data-ttu-id="b036d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b036d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b036d-123">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="b036d-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b036d-124">Kolekcja nagłówków adresu dla punktów końcowych, które można utworzyć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b036d-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="b036d-125">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="b036d-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b036d-126">Korzystając z wystawionego tokenu, określa ustawienia, które umożliwiają klienta do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="b036d-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b036d-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b036d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b036d-128">Element</span><span class="sxs-lookup"><span data-stu-id="b036d-128">Element</span></span>|<span data-ttu-id="b036d-129">Opis</span><span class="sxs-lookup"><span data-stu-id="b036d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b036d-130">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b036d-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="b036d-131">Określa bieżący wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="b036d-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b036d-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b036d-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b036d-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b036d-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b036d-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b036d-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b036d-135">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b036d-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="b036d-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b036d-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b036d-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b036d-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b036d-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b036d-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b036d-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b036d-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b036d-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b036d-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="b036d-141">Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b036d-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="b036d-142">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="b036d-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
