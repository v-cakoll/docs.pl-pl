---
title: <issuerMetadata> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400341"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="0532d-102">\<issuerMetadata > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="0532d-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

<span data-ttu-id="0532d-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0532d-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0532d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0532d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="0532d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="0532d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="0532d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="0532d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="0532d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="0532d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0532d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="0532d-111">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0532d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0532d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0532d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0532d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0532d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0532d-114">Attributes</span></span>  
  
|<span data-ttu-id="0532d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0532d-115">Attribute</span></span>|<span data-ttu-id="0532d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0532d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0532d-117">adres</span><span class="sxs-lookup"><span data-stu-id="0532d-117">address</span></span>|<span data-ttu-id="0532d-118">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="0532d-118">Required.</span></span> <span data-ttu-id="0532d-119">Ciąg określający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0532d-119">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="0532d-120">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="0532d-120">The address must be an absolute URI.</span></span> <span data-ttu-id="0532d-121">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="0532d-121">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0532d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0532d-122">Child Elements</span></span>  
  
|<span data-ttu-id="0532d-123">Element</span><span class="sxs-lookup"><span data-stu-id="0532d-123">Element</span></span>|<span data-ttu-id="0532d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="0532d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0532d-125">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="0532d-125">\<headers></span></span>](headers-element.md)|<span data-ttu-id="0532d-126">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="0532d-126">A collection of address headers.</span></span>|  
|[<span data-ttu-id="0532d-127">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="0532d-127">\<identity></span></span>](identity.md)|<span data-ttu-id="0532d-128">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="0532d-128">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0532d-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0532d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0532d-130">Element</span><span class="sxs-lookup"><span data-stu-id="0532d-130">Element</span></span>|<span data-ttu-id="0532d-131">Opis</span><span class="sxs-lookup"><span data-stu-id="0532d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0532d-132">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="0532d-132">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="0532d-133">Określa parametry tokenu zabezpieczającego wydanego w federacyjnym scenariuszu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0532d-133">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0532d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0532d-134">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0532d-135">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="0532d-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0532d-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0532d-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0532d-137">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="0532d-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0532d-138">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0532d-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0532d-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0532d-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0532d-140">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="0532d-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0532d-141">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0532d-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0532d-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0532d-142">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="0532d-143">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0532d-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="0532d-144">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="0532d-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
