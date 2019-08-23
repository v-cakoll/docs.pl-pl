---
title: <remove><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7238c253bfbc3224c8bbd31265e197dd35e56514
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934239"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="12557-102">\<Usuń > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="12557-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="12557-103">Określa typy oświadczeń do usunięcia w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="12557-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="12557-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12557-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="12557-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="12557-105">\<bindings></span></span>  
<span data-ttu-id="12557-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="12557-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="12557-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="12557-107">\<binding></span></span>  
<span data-ttu-id="12557-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="12557-108">\<security></span></span>  
<span data-ttu-id="12557-109">\<message></span><span class="sxs-lookup"><span data-stu-id="12557-109">\<message></span></span>  
<span data-ttu-id="12557-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="12557-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12557-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="12557-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12557-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12557-112">Attributes and Elements</span></span>  
 <span data-ttu-id="12557-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12557-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12557-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12557-114">Attributes</span></span>  
  
|<span data-ttu-id="12557-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="12557-115">Attribute</span></span>|<span data-ttu-id="12557-116">Opis</span><span class="sxs-lookup"><span data-stu-id="12557-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12557-117">Claim</span><span class="sxs-lookup"><span data-stu-id="12557-117">claimType</span></span>|<span data-ttu-id="12557-118">Identyfikator URI, który definiuje typ żądania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="12557-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12557-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12557-119">Child Elements</span></span>  
 <span data-ttu-id="12557-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="12557-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12557-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12557-121">Parent Elements</span></span>  
  
|<span data-ttu-id="12557-122">Element</span><span class="sxs-lookup"><span data-stu-id="12557-122">Element</span></span>|<span data-ttu-id="12557-123">Opis</span><span class="sxs-lookup"><span data-stu-id="12557-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12557-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="12557-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="12557-125">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="12557-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="12557-126">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="12557-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="12557-127">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="12557-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="12557-128">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="12557-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="12557-129">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="12557-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12557-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12557-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
