---
title: <issuerMetadata> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: d9d7d41277eff1de43f717816b35fdc10d52192e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928877"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="344e7-102">\<issuerMetadata > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="344e7-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="344e7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="344e7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="344e7-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="344e7-104">\<bindings></span></span>  
<span data-ttu-id="344e7-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="344e7-105">\<customBinding></span></span>  
<span data-ttu-id="344e7-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="344e7-106">\<binding></span></span>  
<span data-ttu-id="344e7-107">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="344e7-107">\<security></span></span>  
<span data-ttu-id="344e7-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="344e7-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="344e7-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="344e7-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344e7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="344e7-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="344e7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="344e7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="344e7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="344e7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="344e7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="344e7-113">Attributes</span></span>  
  
|<span data-ttu-id="344e7-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="344e7-114">Attribute</span></span>|<span data-ttu-id="344e7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="344e7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="344e7-116">adres</span><span class="sxs-lookup"><span data-stu-id="344e7-116">address</span></span>|<span data-ttu-id="344e7-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="344e7-117">Required.</span></span> <span data-ttu-id="344e7-118">Ciąg określający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="344e7-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="344e7-119">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="344e7-119">The address must be an absolute URI.</span></span> <span data-ttu-id="344e7-120">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="344e7-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="344e7-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="344e7-121">Child Elements</span></span>  
  
|<span data-ttu-id="344e7-122">Element</span><span class="sxs-lookup"><span data-stu-id="344e7-122">Element</span></span>|<span data-ttu-id="344e7-123">Opis</span><span class="sxs-lookup"><span data-stu-id="344e7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="344e7-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="344e7-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="344e7-125">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="344e7-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="344e7-126">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="344e7-126">\<identity></span></span>](identity.md)|<span data-ttu-id="344e7-127">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="344e7-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="344e7-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="344e7-128">Parent Elements</span></span>  
  
|<span data-ttu-id="344e7-129">Element</span><span class="sxs-lookup"><span data-stu-id="344e7-129">Element</span></span>|<span data-ttu-id="344e7-130">Opis</span><span class="sxs-lookup"><span data-stu-id="344e7-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="344e7-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="344e7-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="344e7-132">Określa parametry tokenu zabezpieczającego wydanego w federacyjnym scenariuszu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="344e7-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="344e7-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="344e7-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="344e7-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="344e7-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="344e7-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="344e7-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="344e7-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="344e7-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="344e7-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="344e7-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="344e7-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="344e7-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="344e7-139">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="344e7-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="344e7-140">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="344e7-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="344e7-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="344e7-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="344e7-142">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="344e7-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="344e7-143">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="344e7-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
