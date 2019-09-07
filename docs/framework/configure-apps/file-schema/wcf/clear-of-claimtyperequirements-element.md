---
title: <clear><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400528"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="2423d-102">\<Wyczyść > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="2423d-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="2423d-103">Określa, że wszystkie typy roszczeń mają być usunięte w poświadczeniu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="2423d-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="2423d-104">Dzięki temu zbieranie danych jest puste.</span><span class="sxs-lookup"><span data-stu-id="2423d-104">This ensures that the collection starts empty.</span></span>  
  
<span data-ttu-id="2423d-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2423d-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2423d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2423d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="2423d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="2423d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2423d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="2423d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> komunikatu**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="2423d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="2423d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="2423d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="2423d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2423d-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="2423d-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2423d-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2423d-115">Attributes and Elements</span></span>  
 <span data-ttu-id="2423d-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2423d-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2423d-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2423d-117">Attributes</span></span>  
 <span data-ttu-id="2423d-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="2423d-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2423d-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2423d-119">Child Elements</span></span>  
 <span data-ttu-id="2423d-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="2423d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2423d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2423d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2423d-122">Element</span><span class="sxs-lookup"><span data-stu-id="2423d-122">Element</span></span>|<span data-ttu-id="2423d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="2423d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2423d-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2423d-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="2423d-125">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="2423d-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="2423d-126">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="2423d-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="2423d-127">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="2423d-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2423d-128">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="2423d-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2423d-129">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="2423d-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2423d-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2423d-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
