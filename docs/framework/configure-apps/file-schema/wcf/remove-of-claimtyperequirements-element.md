---
title: <remove><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399998"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="101c8-102">\<Usuń > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="101c8-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="101c8-103">Określa typy oświadczeń do usunięcia w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="101c8-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
<span data-ttu-id="101c8-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="101c8-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="101c8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="101c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="101c8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="101c8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="101c8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="101c8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> komunikatu**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="101c8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="101c8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="101c8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="101c8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="101c8-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="101c8-113">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="101c8-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="101c8-114">Attributes and Elements</span></span>  
 <span data-ttu-id="101c8-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="101c8-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="101c8-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="101c8-116">Attributes</span></span>  
  
|<span data-ttu-id="101c8-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="101c8-117">Attribute</span></span>|<span data-ttu-id="101c8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="101c8-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="101c8-119">Claim</span><span class="sxs-lookup"><span data-stu-id="101c8-119">claimType</span></span>|<span data-ttu-id="101c8-120">Identyfikator URI, który definiuje typ żądania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="101c8-120">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="101c8-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="101c8-121">Child Elements</span></span>  
 <span data-ttu-id="101c8-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="101c8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="101c8-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="101c8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="101c8-124">Element</span><span class="sxs-lookup"><span data-stu-id="101c8-124">Element</span></span>|<span data-ttu-id="101c8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="101c8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="101c8-126">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="101c8-126">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="101c8-127">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="101c8-127">Specifies a collection of required claim types.</span></span> <span data-ttu-id="101c8-128">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="101c8-128">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="101c8-129">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="101c8-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="101c8-130">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="101c8-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="101c8-131">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="101c8-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="101c8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="101c8-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
