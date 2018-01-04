---
title: '&lt;issuerMetadata&gt; w &lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee0f6b2abe6ddfa81f236da47425ae586b56f0ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="6f2f2-102">&lt;issuerMetadata&gt; w &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="6f2f2-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="6f2f2-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6f2f2-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-104">\<bindings></span></span>  
<span data-ttu-id="6f2f2-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-105">\<customBinding></span></span>  
<span data-ttu-id="6f2f2-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-106">\<binding></span></span>  
<span data-ttu-id="6f2f2-107">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-107">\<security></span></span>  
<span data-ttu-id="6f2f2-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="6f2f2-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f2f2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f2f2-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f2f2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6f2f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6f2f2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f2f2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6f2f2-113">Attributes</span></span>  
  
|<span data-ttu-id="6f2f2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6f2f2-114">Attribute</span></span>|<span data-ttu-id="6f2f2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6f2f2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f2f2-116">adres</span><span class="sxs-lookup"><span data-stu-id="6f2f2-116">address</span></span>|<span data-ttu-id="6f2f2-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-117">Required.</span></span> <span data-ttu-id="6f2f2-118">Ciąg określający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="6f2f2-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-119">The address must be an absolute URI.</span></span> <span data-ttu-id="6f2f2-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f2f2-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6f2f2-121">Child Elements</span></span>  
  
|<span data-ttu-id="6f2f2-122">Element</span><span class="sxs-lookup"><span data-stu-id="6f2f2-122">Element</span></span>|<span data-ttu-id="6f2f2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6f2f2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f2f2-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="6f2f2-125">Kolekcja nagłówków adresu.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="6f2f2-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="6f2f2-127">Tożsamości, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f2f2-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6f2f2-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6f2f2-129">Element</span><span class="sxs-lookup"><span data-stu-id="6f2f2-129">Element</span></span>|<span data-ttu-id="6f2f2-130">Opis</span><span class="sxs-lookup"><span data-stu-id="6f2f2-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f2f2-131">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="6f2f2-132">Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f2f2-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f2f2-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="6f2f2-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="6f2f2-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="6f2f2-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="6f2f2-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6f2f2-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6f2f2-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="6f2f2-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="6f2f2-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6f2f2-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6f2f2-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6f2f2-139">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="6f2f2-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6f2f2-140">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6f2f2-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6f2f2-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6f2f2-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="6f2f2-142">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6f2f2-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="6f2f2-143">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="6f2f2-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
