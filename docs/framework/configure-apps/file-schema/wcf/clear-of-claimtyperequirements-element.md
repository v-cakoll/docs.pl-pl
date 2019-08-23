---
title: <clear><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: e7e3bebd85decbaa4d216743f9bea9e135b87995
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926137"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="f238b-102">\<Wyczyść > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="f238b-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="f238b-103">Określa, że wszystkie typy roszczeń mają być usunięte w poświadczeniu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="f238b-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="f238b-104">Dzięki temu zbieranie danych jest puste.</span><span class="sxs-lookup"><span data-stu-id="f238b-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="f238b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f238b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f238b-106">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="f238b-106">\<bindings></span></span>  
<span data-ttu-id="f238b-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="f238b-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="f238b-108">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f238b-108">\<binding></span></span>  
<span data-ttu-id="f238b-109">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f238b-109">\<security></span></span>  
<span data-ttu-id="f238b-110">\<message></span><span class="sxs-lookup"><span data-stu-id="f238b-110">\<message></span></span>  
<span data-ttu-id="f238b-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="f238b-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f238b-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f238b-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f238b-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f238b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f238b-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f238b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f238b-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f238b-115">Attributes</span></span>  
 <span data-ttu-id="f238b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f238b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f238b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f238b-117">Child Elements</span></span>  
 <span data-ttu-id="f238b-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="f238b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f238b-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f238b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f238b-120">Element</span><span class="sxs-lookup"><span data-stu-id="f238b-120">Element</span></span>|<span data-ttu-id="f238b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f238b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f238b-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="f238b-122">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="f238b-123">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="f238b-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="f238b-124">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="f238b-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="f238b-125">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="f238b-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="f238b-126">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="f238b-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="f238b-127">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="f238b-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f238b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f238b-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
