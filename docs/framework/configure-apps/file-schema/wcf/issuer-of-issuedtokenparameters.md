---
title: <issuer> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 77ed9534ce872e805a6a6ea2c21a38710e6bc0fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925267"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="3718d-102">\<wystawca > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="3718d-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="3718d-103">Określa usługę tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="3718d-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="3718d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3718d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3718d-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="3718d-105">\<bindings></span></span>  
<span data-ttu-id="3718d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3718d-106">\<customBinding></span></span>  
<span data-ttu-id="3718d-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="3718d-107">\<binding></span></span>  
<span data-ttu-id="3718d-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="3718d-108">\<security></span></span>  
<span data-ttu-id="3718d-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="3718d-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="3718d-110">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="3718d-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3718d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="3718d-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3718d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3718d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3718d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3718d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3718d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3718d-114">Attributes</span></span>  
  
|<span data-ttu-id="3718d-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3718d-115">Attribute</span></span>|<span data-ttu-id="3718d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3718d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3718d-117">adres</span><span class="sxs-lookup"><span data-stu-id="3718d-117">address</span></span>|<span data-ttu-id="3718d-118">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="3718d-118">Required string.</span></span> <span data-ttu-id="3718d-119">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="3718d-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3718d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3718d-120">Child Elements</span></span>  
  
|<span data-ttu-id="3718d-121">Element</span><span class="sxs-lookup"><span data-stu-id="3718d-121">Element</span></span>|<span data-ttu-id="3718d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3718d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3718d-123">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="3718d-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="3718d-124">Kolekcja nagłówków adresów dla punktów końcowych, które może utworzyć Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3718d-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="3718d-125">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="3718d-125">\<identity></span></span>](identity.md)|<span data-ttu-id="3718d-126">W przypadku korzystania z wystawionego tokenu określa ustawienia, które umożliwiają klientowi uwierzytelnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="3718d-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3718d-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3718d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3718d-128">Element</span><span class="sxs-lookup"><span data-stu-id="3718d-128">Element</span></span>|<span data-ttu-id="3718d-129">Opis</span><span class="sxs-lookup"><span data-stu-id="3718d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3718d-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="3718d-130">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="3718d-131">Określa bieżący token wystawiony.</span><span class="sxs-lookup"><span data-stu-id="3718d-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3718d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3718d-132">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3718d-133">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="3718d-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3718d-134">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="3718d-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3718d-135">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3718d-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3718d-136">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="3718d-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3718d-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3718d-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3718d-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="3718d-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3718d-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="3718d-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3718d-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3718d-140">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="3718d-141">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3718d-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="3718d-142">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="3718d-142">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
