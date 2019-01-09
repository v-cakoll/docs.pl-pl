---
title: '&lt;issuerMetadata&gt; w &lt;issuedTokenParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 76956c54739219bbde78f378a12d59563ab785c4
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148750"
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="6f68e-102">&lt;issuerMetadata&gt; w &lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="6f68e-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="6f68e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6f68e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6f68e-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="6f68e-104">\<bindings></span></span>  
<span data-ttu-id="6f68e-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6f68e-105">\<customBinding></span></span>  
<span data-ttu-id="6f68e-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="6f68e-106">\<binding></span></span>  
<span data-ttu-id="6f68e-107">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6f68e-107">\<security></span></span>  
<span data-ttu-id="6f68e-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="6f68e-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="6f68e-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="6f68e-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f68e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f68e-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f68e-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6f68e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6f68e-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6f68e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f68e-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6f68e-113">Attributes</span></span>  
  
|<span data-ttu-id="6f68e-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6f68e-114">Attribute</span></span>|<span data-ttu-id="6f68e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6f68e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f68e-116">adres</span><span class="sxs-lookup"><span data-stu-id="6f68e-116">address</span></span>|<span data-ttu-id="6f68e-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6f68e-117">Required.</span></span> <span data-ttu-id="6f68e-118">Ciąg, który określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6f68e-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="6f68e-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="6f68e-119">The address must be an absolute URI.</span></span> <span data-ttu-id="6f68e-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="6f68e-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f68e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6f68e-121">Child Elements</span></span>  
  
|<span data-ttu-id="6f68e-122">Element</span><span class="sxs-lookup"><span data-stu-id="6f68e-122">Element</span></span>|<span data-ttu-id="6f68e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6f68e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f68e-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="6f68e-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="6f68e-125">Kolekcję nagłówków adresowych.</span><span class="sxs-lookup"><span data-stu-id="6f68e-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="6f68e-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="6f68e-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="6f68e-127">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="6f68e-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f68e-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6f68e-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6f68e-129">Element</span><span class="sxs-lookup"><span data-stu-id="6f68e-129">Element</span></span>|<span data-ttu-id="6f68e-130">Opis</span><span class="sxs-lookup"><span data-stu-id="6f68e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f68e-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="6f68e-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="6f68e-132">Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="6f68e-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f68e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f68e-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="6f68e-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="6f68e-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="6f68e-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="6f68e-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6f68e-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6f68e-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="6f68e-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="6f68e-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6f68e-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6f68e-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6f68e-139">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="6f68e-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6f68e-140">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6f68e-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6f68e-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6f68e-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="6f68e-142">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6f68e-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="6f68e-143">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="6f68e-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
