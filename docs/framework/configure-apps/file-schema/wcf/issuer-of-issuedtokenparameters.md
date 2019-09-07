---
title: <issuer> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397943"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="25728-102">\<wystawca > \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="25728-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="25728-103">Określa usługę tokenu zabezpieczającego (STS), która wystawia tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="25728-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="25728-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="25728-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="25728-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="25728-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="25728-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="25728-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="25728-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="25728-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="25728-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="25728-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="25728-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="25728-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="25728-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="25728-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="25728-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> wystawcy**</span><span class="sxs-lookup"><span data-stu-id="25728-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25728-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="25728-112">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25728-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25728-113">Attributes and Elements</span></span>  
 <span data-ttu-id="25728-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25728-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25728-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25728-115">Attributes</span></span>  
  
|<span data-ttu-id="25728-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="25728-116">Attribute</span></span>|<span data-ttu-id="25728-117">Opis</span><span class="sxs-lookup"><span data-stu-id="25728-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25728-118">adres</span><span class="sxs-lookup"><span data-stu-id="25728-118">address</span></span>|<span data-ttu-id="25728-119">Wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="25728-119">Required string.</span></span> <span data-ttu-id="25728-120">Adres URL usługi STS.</span><span class="sxs-lookup"><span data-stu-id="25728-120">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25728-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25728-121">Child Elements</span></span>  
  
|<span data-ttu-id="25728-122">Element</span><span class="sxs-lookup"><span data-stu-id="25728-122">Element</span></span>|<span data-ttu-id="25728-123">Opis</span><span class="sxs-lookup"><span data-stu-id="25728-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25728-124">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="25728-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="25728-125">Kolekcja nagłówków adresów dla punktów końcowych, które może utworzyć Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="25728-125">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="25728-126">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="25728-126">\<identity></span></span>](identity.md)|<span data-ttu-id="25728-127">W przypadku korzystania z wystawionego tokenu określa ustawienia, które umożliwiają klientowi uwierzytelnienie serwera.</span><span class="sxs-lookup"><span data-stu-id="25728-127">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25728-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25728-128">Parent Elements</span></span>  
  
|<span data-ttu-id="25728-129">Element</span><span class="sxs-lookup"><span data-stu-id="25728-129">Element</span></span>|<span data-ttu-id="25728-130">Opis</span><span class="sxs-lookup"><span data-stu-id="25728-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25728-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="25728-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="25728-132">Określa bieżący token wystawiony.</span><span class="sxs-lookup"><span data-stu-id="25728-132">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25728-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25728-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="25728-134">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="25728-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="25728-135">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="25728-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="25728-136">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="25728-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="25728-137">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="25728-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="25728-138">Powiązania</span><span class="sxs-lookup"><span data-stu-id="25728-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25728-139">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="25728-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="25728-140">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="25728-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="25728-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="25728-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="25728-142">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="25728-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="25728-143">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="25728-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
